---
title: "samba conf for two shared folder with and without authentication?"
date: 2006-08-01
forum: Desktop Environments
---

### Post by hudanet2005 on 2006-08-01
i have a computer with two (2) shared folders. 
from ubuntu dapper guide i can share these two folders with or without authentication

the problem is that when i want to share one folder with authentication and another without authentication. 

there is conflict in samba.conf 
the configuration for folder with authentication is

  security = user
  username map = /etc/samba/smbusers

the configuration for folder without authentication is

  security = share

is it possible to share folders which we can share with and without authentication working in the same computer?????

help me please

---

### Post by cage cat donnie on 2006-10-24
I am also needing a solution to this.

Thanks.

---

### Post by Aikinai on 2006-11-01
I also have the same question. This seems pretty important and I can't believe there's not a way to do it.

---

### Post by jmaryinchina on 2008-01-13
I have proceeded the following modifications to gain a folder where everybody can/read write without authentication.

Do this : 

> mkdir /home/sharing

Now we can make this folder has read/write access for everybody, but only file owner can modify his own files. This is usefull to put here some files which can be modified/deleted.

> chmod 1777

Then in /etc/smb.conf do :

be sure to have those : (replace WORKGROUP with your windows network name)

>    workgroup = WORKGROUP

Be sure that you network interfaces are delivering the service :

>    interfaces = 127.0.0.0/8 eth0 eth1

Change the following to be as shown :

>    security = share
   guest account = nobody

 Then at the bottom, add :

> [SHARING]
path = /home/sharing
comment = Read/Write to Everybody
valid users =
write list =
admin users =
create mode = 0700
read only = no
writable = yes
guest ok = yes
public = yes
printable = no
share modes = yes
locking = no

Then /etc/init.d/samba restart
The folder /home/sharing is now granted read/write access without authentication.

---

