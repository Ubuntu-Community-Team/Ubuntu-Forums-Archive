---
title: "mysterious filesystems"
date: 2006-09-22
forum: Desktop Environments
---

### Post by outtacontrol on 2006-09-22
Can anyone tell me what these filesystems are used for?  I didn't create them:

```
varrun                  257968       148    257820   1% /var/run
varlock                 257968         4    257964   1% /var/lock
udev                    257968       100    257868   1% /dev
```

They do not show up in my fstab file:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /boot           ext3    defaults        0       2
/dev/mapper/Ubuntu-swap_1 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

Any ideas??

outta.

---

