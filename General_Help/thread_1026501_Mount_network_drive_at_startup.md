---
title: "Mount network drive at startup"
date: 2008-12-31
forum: General Help
---

### Post by dave_didlydodo on 2008-12-31
I'm using an Linksys NSLU2 device plus a USB drive to give me network storage on my home LAN. I've managed to configure SBACKUP to do full and incremental backups to the drive but I'd like to know how to mount it automatically at startup. I assume this is done by editing fstab but I don't know what to put in it.

The drive is location is:

smb://netstore/disk%201/  or smb://netstore/disk 1/ and the filesystem type is cifs.

Help!

---

### Post by albandy on 2008-12-31
add this to /etc/fstab

//netstore/disk1 /media/disk1 smbfs dmask=777,username=username,password=password  0  0

if your netstore dont use password remove username=username and password=password

---

### Post by dave_didlydodo on 2008-12-31
Thanks albandy, I'll give it a go.

---

