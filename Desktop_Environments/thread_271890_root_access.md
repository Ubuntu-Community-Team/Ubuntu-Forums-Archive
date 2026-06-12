---
title: "root access"
date: 2006-10-05
forum: Desktop Environments
---

### Post by astral69 on 2006-10-05
I am not quite ready to make Ubuntu my default system so I want to change the boot menu file /boot/grub/menu.lst.
The problem is the file belongs to root and other users cannot modify, only read.
So what is the root password?
In other distros I have always been allowed to add root as the first user during installation.
If I do that here the login screen tells me that root access is not allowed to login on the graphics interface.
If I cannot login then I cannot add other users.
If I specify another id at installation, say admin, then I have no root access.
I am stumped on this one.

Thanks

---

### Post by ardchoille on 2006-10-05
> **astral69 said:**
> I am not quite ready to make Ubuntu my default system so I want to change the boot menu file /boot/grub/menu.lst.
The problem is the file belongs to root and other users cannot modify, only read.
So what is the root password?
In other distros I have always been allowed to add root as the first user during installation.
If I do that here the login screen tells me that root access is not allowed to login on the graphics interface.
If I cannot login then I cannot add other users.
If I specify another id at installation, say admin, then I have no root access.
I am stumped on this one.

Thanks

The root account is locked for security reasons and you really don't need to use it. If you want to read/edit that file, open a term and type

gksudo gedit /boot/grub/menu.lst  (for gui apps, use gksudo)

OR

sudo vim /boot/grub/menu.lst (for command line apps, use sudo)

there really is no need to enable the root account because everything you need to do can be done via sudo/gksudo (ex. 'gksudo nautilus' will open nautilus as if root had opened it) and having the root account makes your box more secure. A cracker can't brute force the root password if the root account is disabled and they can't brute force the user accounts because they don't know the usernames. I've been using Ubuntu since warty and have never needed to enable the root account.. it just isn't necessary.

---

### Post by aysiu on 2006-10-05
Read these two links:
[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by astral69 on 2006-10-06
Thanks:p

---

