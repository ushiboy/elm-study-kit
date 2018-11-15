# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"
  config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.network "forwarded_port", guest: 8000, host: 8000
  # config.vm.network "private_network", ip: "192.168.33.10"
  # config.vm.network "public_network"
  # config.vm.provider "virtualbox" do |vb|
  #   vb.cpus = 2
  #   vb.memory = "2048"
  # end
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y curl sudo
    curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -
    sudo apt-get install -y nodejs
    sudo npm install -g elm elm-format --unsafe-perm=true --allow-root
    ln -s /vagrant/ /home/vagrant/elm-workspace
  SHELL
end
