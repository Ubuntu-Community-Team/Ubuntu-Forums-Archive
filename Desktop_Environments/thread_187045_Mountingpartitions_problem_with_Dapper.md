---
title: "Mounting/partitions problem with Dapper"
date: 2006-06-02
forum: Desktop Environments
---

### Post by PtS on 2006-06-02
When I installed Dapper I repartitioned my root partition leaving my home partition as it was. Something must have gone wrong because all the objects in Places -> Computer is owned by unknown. This isn't really a problem (even if it may have something to do with the real problem). The problem is that my CDs doesn't automount. It mounts only when i try to open it through Places -> Computer and I have to open /media/cdrom0 to get to the cd. Does anybody know how to fix this?

EDIT: I can't mount USBs at all.

---

### Post by Crooksey on 2006-06-02
Could you post your fstab file (loacted @ /etc/fstab)

---

### Post by PtS on 2006-06-03
As far as i know, my fstab is alright.
Anyway... My fstab (I have a swedish system):

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda10      /               reiserfs defaults        0       1
/dev/hda8       /boot           ext2    defaults        0       2
/dev/hda11      /home           reiserfs defaults        0       2
/dev/hda7       /media/övrigt    vfat    iocharset=utf8,umask=000,gid=46 0       1
/dev/hda5       /media/program  vfat    iocharset=utf8,umask=000,gid=46 0       1
/dev/hda6       /media/spel     ntfs    nls=utf8,umask=0222,gid=46 0       1
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222,gid=46 0       1
/dev/hda9       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

EDIT: Suddenly it works. Don't know why.

---

