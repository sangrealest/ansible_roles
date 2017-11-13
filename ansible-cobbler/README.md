Cobbler
=======

This role is used to deploy cobbler.

Role Variables
--------------

```
---

### cobbler server
cobbler_password: "p@ssw0rd" # default root password for new kicked servers
cobbler_manage_dhcp: 1 # Call cobbler to manage dhcp service, set to 0 if not.
cobbler_pxe_just_once: 1

#Cobbler server network settings, if not defined, will use target servers default facts
cobbler_server: 172.16.170.7
cobbler_next_server: 172.16.170.7

#Cobbler server dhcp.template settings
cobbler_subnet: 172.16.170.0
cobbler_netmask: 255.255.255.0
cobbler_routers: 172.16.170.7
cobbler_domain_name_servers: 223.5.5.5
cobbler_subnet_mask: 255.255.255.0
cobbler_dynamic_bootp_start: 172.16.170.100
cobbler_dynamic_bootp_end: 172.16.170.250

#Cobbler web admin account settings
cobbler_web_pwd: "caac501fc46894f400a322bc2297a483" # use command to generate passwd: 'htdgist /etc/cobbler/users.digest "Cobbler" cobbler'


iso_name: rhel-server-7.4-x86_64-dvd.iso

# Distribution info
cobbler_distros:
  - distro_name: RHEL7
    device_or_iso_path: /var/iso_images
    arch: x86_64
    kickstart_file_name: rhel7_virtual.cfg


```





The example of inventory file is:

```
[lab]
lab01
```




Example Playbook
----------------

```
---
- hosts: lab
  gather_facts: true
  strategy: debug
  roles:
    - ansible-cobbler

```


License
-------

MIT
