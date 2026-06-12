---
title: "HAL Initialization Failure - but I don't think I have samba shares"
date: 2006-07-06
forum: Desktop Environments
---

### Post by richardq on 2006-07-06
I'm getting a message upon bootup that "HAL initialization failed". I've done a bit of reading at it appears to be a problem with auto-mounting samba shares. First of all I don't have a clue what a samba share is, and I'm pretty sure I don't have any :) . Here is my fstab. Anybody know how I can work around the problem. It's quite slow getting to the desktop, but it doesn't seem to affect much else.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb2       /home           ext3    defaults        0       2
/dev/hdb1       /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda6       /osshare        vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

---

