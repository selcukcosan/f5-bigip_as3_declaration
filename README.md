# f5-bigip_as3_declaration

This Ansible script writes AS3 Declaration json file into F5 BIG-IP devices via REST. The script uses the official f5networks.f5_bigip Ansible modules on [https://galaxy.ansible.com/ui/repo/published/f5networks/f5_modules/](https://galaxy.ansible.com/ui/repo/published/f5networks/f5_bigip/)

The inventory yaml format is simple as below.


```yml
---
all:
  children:
    all_f5:
      hosts:
        bigip1:
          inventory_network_os: f5.bigip
          inventory_host: 192.168.1.245
          inventory_port: 443
          inventory_user: admin
          inventory_pass: password
        bigip2:
          inventory_network_os: f5.bigip
          inventory_host: 192.168.1.246
          inventory_port: 443
          inventory_user: admin
          inventory_pass: password
        bigip11:
          inventory_network_os: f5.bigip
          inventory_host: 192.168.1.231
          inventory_port: 443
          inventory_user: admin
          inventory_pass: password
```

## Prerequisite
F5 Ansible Declarative Modules must be installed before running the script.
```bash
ansible-galaxy collection install f5networks.f5_bigip==3.2.2
```

## Usage:
```bash

ANSIBLE_HOST_KEY_CHECKING=False ansible-playbook -vvvv --vault-password-file vault_pass.yaml -i inventory-vault.yaml bigip11_as3_basics.yaml --extra-vars="bigip=bigip11"
```

## Files
- bigip11_as3_basics.yaml >> Ansible script file
- declarations/bigip11_as3.json >> AS3 Declaration File
- vault_pass.yaml >> Inventory vault password information
- inventory-vault.yaml >> Inventory vault file encrypted by "Inventory vault password"
