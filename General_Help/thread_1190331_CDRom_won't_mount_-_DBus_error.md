---
title: "CDRom won't mount - DBus error?"
date: 2009-06-17
forum: General Help
---

### Post by loserboy on 2009-06-17
trying to access some data discs someone gave me at work, a momnet after I insert a CD this is the message I get:

```
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```


fstab contents:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=ac91f103-9f50-49dd-af49-f2960a66e31a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=AEDC22C9DC228C21 /media/XP       ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=401E-B464  /media/backup_1 vfat    utf8,umask=007,gid=46 0       1
# /dev/sdb6
UUID=909D-7724  /media/backup_2 vfat    utf8,umask=007,gid=46 0       1
# /dev/sdb7
UUID=fe4e5cf6-7d61-4a9f-942a-ade5c59a6c4d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0



help?

---

