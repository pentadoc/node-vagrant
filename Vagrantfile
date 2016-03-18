# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "ubuntu/trusty64"

  config.vm.hostname = "node-vagrant-machine"

  # Add port-forward for Express apps
  config.vm.network "forwarded_port", guest: 3000, host: 3000
  # Add port-forward for Node-inspector
  config.vm.network "forwarded_port", guest: 5858, host: 5858
  # Add port-forward for Sails.js apps
  config.vm.network "forwarded_port", guest: 1337, host: 1337
  # Add port-forward for other example apps
  config.vm.network "forwarded_port", guest: 8000, host: 8000
  # Add port-forward for Webpack
  config.vm.network "forwarded_port", guest: 8080, host: 8080

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network "private_network", ip: "192.168.33.20"

  # Shared folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  config.vm.synced_folder "dev", "/home/vagrant/dev", create: true

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # VirtualBox:
  config.vm.provider "virtualbox" do |vb|
     # Boot with headless mode
     vb.gui = false

     # Use VBoxManage to customize the VM. For example to change memory:
     vb.customize ["modifyvm", :id, "--memory", "2048"]
  end

  # Enable provisioning with Puppet stand alone.  Puppet manifests
  # are contained in a directory path relative to this Vagrantfile.
  config.vm.provision "puppet" do |puppet|
    puppet.manifests_path = "puppet/manifests"
    puppet.manifest_file  = "default.pp"
    puppet.module_path = "puppet/modules"
  end
end
