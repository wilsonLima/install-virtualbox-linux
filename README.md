install-virtualbox-linux
=========

Role do Ansible com os passos para a instalação do VirtualBox em distribuições Linux.

Distribuições Suportadas pela Role
------------

- Fedora 28 ou superior
- Linux Mint LMDE 3 (64 bits) ou superior
- Linux Mint 19.2 (64 bits) ou superior
- openSUSE Leap 15.0 ou superior
- Ubuntu 19.04 (64 bits) ou superior


Tags da Role 
--------------

- main: Tag a ser utilizada em conjunto com outras tags, se alguma tag for especificada no comando.
  
- repo: Inclui todos os repositórios da role no Sistema.
- deps: Instala os pacotes de dependências.

- virtualbox: Realiza a instalação do VirtualBox.
- vagrant: Realiza a instalação do Vagrant.


Variáveis da Role 
--------------

- vagrant_version: Versão do Vagrant, valor padrão: 2.2.18 .
- virtualbox_version: versão do VirtualBox, valor padrão: 6.1 .


Dependências da Role 
--------------

Linux Mint e Ubuntu:

- openssh-server. Ex.: sudo apt install openssh-server


Exemplo de Inventario
----------------

Exemplo de arquivo de hosts: pasta_invetario/hosts

    [NOME]
    IP ansible_connection=ssh ansible_ssh_user=USUARIO ansible_ssh_pass=SENHA_URUARIO ansible_become_pass=SENHA_ROOT


Especificar interpretador python 3: pasta_invetario/group_vars/all

    ansible_python_interpreter: "/usr/bin/python3"


Exemplo de Playbook
----------------

Exemplo de uso da Role, com as configurações padrão:

    - hosts: desktop
      roles:
         - install-virtualbox-linux

Exemplo de uso da Role com variáveis:

    - hosts: desktop
      roles:
         - { role: install-virtualbox-linux, virtualbox_version: 6.0 }


Exemplo de Comandos
----------------

Comando para executar todas as tasks:

    ansible-playbook -i <caminho_inventario> <caminho_playbook>

Comando para executar a tag "vagrant" (em caso de uso de tags, a tag "main" é obrigatória):

    ansible-playbook -i <caminho_inventario> <caminho_playbook> --tags "main, vagrant"


License
-------

MIT