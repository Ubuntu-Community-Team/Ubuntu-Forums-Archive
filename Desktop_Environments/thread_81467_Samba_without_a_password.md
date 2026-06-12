---
title: "Samba without a password"
date: 2005-10-24
forum: Desktop Environments
---

### Post by kreso on 2005-10-24
How can I share my home folder on my LAN without others having to type a username & password to access it?

---

### Post by cwaldbieser on 2005-10-24
[QUOTE=kreso]How can I share my home folder on my LAN without others having to type a username & password to access it?[/QUOTE]

1) Backup your /etc/samba/smb.conf
2) Edit smb.conf.  Change/add the following:

```

[global]
    workgroup = <workgroup>
    netbios name = <netbios name>
    server string = <server string>
    security = share
    browsable = yes
    hosts allow = 192.168.1.

[share1]
    path = <path to share>
    comment = <comment>
    read only = No
    guest ok = Yes

```

The stuff in angle brackets should mostly be self explanitory.  The 192.168.1 network is typical for home networks, but you might need to put your own network numbers in.  The netbios name must be <= 15 characters.  The share name should be <= 12 characters.  Make sure you set the folder permissions on the share to 777 (all permissions for everyone).

One note, this is ultra permissive-- it lets anyone read/write to the share.

---

