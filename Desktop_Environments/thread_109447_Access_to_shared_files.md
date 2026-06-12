---
title: "Access to shared files"
date: 2005-12-28
forum: Desktop Environments
---

### Post by Dearhell on 2005-12-28
I can write my Ubuntu shared directory from a windows machine of my network, but when from Ubuntu I put some file on my shared directory, it has no enough permissions, and then I can't copy that file from the Windows machine

And I don't want to give permissions to each file I put in my Ubuntu's shared folder

---

### Post by Dearhell on 2005-12-29
The share definitions of smb.conf: 

```
#======================= Share Definitions =======================

wins support = no
[homes]
   comment = Home Directories
   browseable = yes

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

[emule]
   comment = Emule
   path = /home/casa/.aMule/Incoming
   public = yes
   writable = yes
   create mode = 0775
   directory mode = 0775
   read only = no
   public = yes
   browseable = yes
```

---

