# Ansible Collection - ryangorden.cisco_ios

Documentation for the collection.

## Installing this collection

You can install this example collection with the Ansible Galaxy CLI (https or ssh):

    ansible-galaxy collection install git+https://github.com/ryangorden/Collection-Example.git
    ansible-galaxy collection install git@github.com:ryangorden/Collection-Example.git

You can also include it in a "requirements.yml" file and install it with "ansible-galaxy collection install -r requirements.yml", using the format. The branch can be used as the version and it represented at the end of the git uri with the ",<branch_name>:


    ---
    collections:
      - name: https://github.com/ryangorden/Collection-Example.git,main
        type: git


A specific version of the collection can be installed by using the version keyword in the requirements.yml file. The version value is the sha value of a git commit:


    ---
    collections:
      - name: https://github.com/ryangorden/Collection-Example.git
        type: git
        version: 82f04a777d18e6a3feda7dece99c729816b30c63

## Using the collection

You can a call role by their Fully Qualified Collection Namespace (FQCN), such as ryangorden.cisco_ios.ios_backup, or you can call roles by their short name if you list the ryangorden.cisco_ios collection in the playbook's collections keyword:

    ---
    - name: get version
      connection: network_cli
      gather_facts: false
      hosts: routers
      vars:
        ansible_ssh_common_args: "-o StrictHostKeyChecking=no -o Ciphers=+aes256-cbc -o KexAlgorithms=+diffie-hellman-group14-sha1,diffie-hellman-group1-sha1"
      tasks:
        - name: backup ios device
          ansible.builtin.include_role:
              name: "ryangorden.cisco.ios_backup"
          when: ansible_network_os == "ios"
