---
title: "Mounting windows shares in linux."
date: 2005-01-08
forum: Desktop Environments
---

### Post by tvlad on 2005-01-08
I know i can mount shares in linux using the mount -t smbf...... command, my question is how if possible can i edit the /etc/fstab in order for the share to be mounted each time the windows pc is up.

I know i could place the whole mount command in /etc/local.conf, but i'm asking if it's not possible to edit the FSTAB in order to do it. 

Thx.

---

### Post by labbe on 2005-01-08
```
$ sudo gedit /etc/fstab
```
And just edit

---

### Post by tvlad on 2005-01-08
That's what i did : //share/music          /mnt           smbfs   defaults,user,exec

My only question is if i can specify the password here as well.

---

### Post by labbe on 2005-01-08
if I understood you, take a look [here](http://www.ubuntuguide.org/#automountnetworkfolder)

---

### Post by tiiim on 2005-01-08
[QUOTE=tvlad]That's what i did : //share/music          /mnt           smbfs   defaults,user,exec

My only question is if i can specify the password here as well.[/QUOTE]
 you needed to edit that file as root is that wot u you mean?

---

### Post by tvlad on 2005-01-08
Thx labbe, that did the trick, and the site as a whole is really, really useful.
Thx again guys for all the help.

---

