# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # Definir la máquina virtual
  config.vm.box = "ubuntu/focal64"  # Ubuntu 20.04 LTS
  config.vm.hostname = "ansible-flask"

  # Configurar red privada
  config.vm.network "private_network", type: "dhcp"

  # Sincronizar archivos locales
  config.vm.synced_folder "./", "/vagrant", type: "virtualbox"

  # Incrementar timeout de SSH para inicio lento
  config.vm.boot_timeout = 600

  # Provisión para instalar dependencias
  config.vm.provision "shell", inline: <<-SHELL
    # Actualizar paquetes
    apt-get update

    # Instalar Ansible
    apt-get install -y ansible python3-pip

    # Confirmar instalación
    ansible --version

    # Configurar permisos para archivos
    chmod -R 755 /vagrant
  SHELL

  # Configurar recursos de la máquina virtual
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
    vb.cpus = 2
  end
end
