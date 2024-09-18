# Ansible Playbook: Bulk Create VM on Proxmox

## How to use?

1. Copy example inventories to your favor name

    ```sh
    cp -r inventories/example inventories/<inventory-name>
    ```

2. Change the inventory config in `ansible.cfg`

    ```toml
    [defaults]
    inventory=inventories/<inventory-name>
    ```

3. Update `inventories/<inventory-name>/all.var`

    1. Change proxmox identity

        - `proxmox_user`: the user who create the API key. e.g. `root@pam`
        - `proxmox_token`: the token name. (!IMPORTANT: should not include the `proxmox_user`)
        - `proxmox_token_secret`: the token secret
        - `proxmox_host`: the proxmox api endpoint

    2. Update VM List

        - `vmid`: the VM ID
        - `name`: name of the VM
        - `proxmox_node`: the proxmox node where the VM will be created
        - `clone_vmid`: the template VM ID
        - `storage`: the storage unique name where the VM will be stored
        - `cpus`: the number of CPU cores
        - `memory`: the memory size of the VM
        - `disk_size`: the disk size of the VM
        - `sshkeys`: the ssh public key to be injected to the VM (multiple keys should be separated by newline)
        - `net`: the network configuration of the VM
            - `ip`: the IP address of the VM including CIDR (e.g. `10.216.100.60/24`)
            - `gw`: the gateway of the VM (e.g. `10.216.0.1`)
