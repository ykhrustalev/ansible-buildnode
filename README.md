Role Name
=========

Build node, currently debian, able to provide dependencies for

* python 
* postgresql

Installation
------------

    ansible-galaxy install ykhrustalev.buildnode

Requirements
------------

Debian version >= 6

Role Variables
--------------

To install repos list, define (based on ykhrustalev.basenode role)

    basenode_codename: jessie
    basenode_install_repos: true

Which user going to be infra owner 

    buildnode_user: '{{ansible_ssh_user}}'


To install python dependencies

    buildnode_postgresql: true

To install python dependencies

    buildnode_python: false
    buildnode_python_wheelhouse: /var/wheelhouse
    
Optional:

    buildnode_dh_virtualenv_version: 0.9-1
    buildnode_dh_virtualenv_sha256: 1878efb2c5742d27530a5325c6e600883c782b4d7812256f4f19b98d48331111
    buildnode_dh_virtualenv_name: dh-virtualenv_{{buildnode_dh_virtualenv_version}}_all.deb
    buildnode_dh_virtualenv_url: http://cdn.debian.net/debian/pool/main/d/dh-virtualenv/{{buildnode_dh_virtualenv_name}}

    
Dependencies
------------

    dependencies:
      - role: ykhrustalev.basenode

Example Playbook
----------------

To use add

    - hosts: servers
      roles:
        - {role: ykhrustalev.buildnode,
           buildnode_python: true,
           buildnode_postgresql: true}


License
-------

MIT

Author Information
------------------

Yuri Khrustalev
