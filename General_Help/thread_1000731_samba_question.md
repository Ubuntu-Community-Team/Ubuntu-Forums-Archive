---
title: "samba question"
date: 2008-12-03
forum: General Help
---

### Post by fouadk on 2008-12-03
hi everyone....

i have a machine setup with samba and winbind...

what i am trying to is that i have a share that i need when a winbind user creates a folder or file in it i want the permission to be automatically set to 700 and with username:root privileges

this is the share definition:


```

[PHA204]
comment = PHA204
path = /home/tazmaster/resources/PHA204
read only = No
create mask = 0700
directory mask = 0700
browsable = yes
map hidden = no
map archive = yes
map system = yes
public = Yes
writeable = Yes
guest ok = no
inherit permissions = no
nt acl support = yes


```

please help

thanks in advance

---

