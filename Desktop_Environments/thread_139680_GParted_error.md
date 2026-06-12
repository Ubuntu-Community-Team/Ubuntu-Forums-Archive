---
title: "GParted error"
date: 2006-03-04
forum: Desktop Environments
---

### Post by Cirrocco on 2006-03-04
when I open GParted I get this:
> 
The kernel is unable to re-read the partition tables on the following devices:
- /dev/mapper/Ubuntu-root

Because of this, you will only have limited access to these devices.
Unmount all mounted partitions on a device to get full access.


when I look at my root drive:
/dev/hdb1 -ext3 (boot)
/dev/hdb2 -extended
   /dev/hdb5 -unknown (lvm)

when I look at my device list I have these two entries:
/dev/mapper/ubuntu-swap_1 (3028 MB)
/dev/mapper/ubuntu_root (73038 MB)

when I click these devices I see their info:
swap is listed as linux swap
root is listed as reiserfs

fresh install of Ubuntu, why would I be getting this error? why don't my devices show up properly?

---

### Post by Cirrocco on 2006-03-04
here's my fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               reiserfs defaults        0       1
/dev/hdb1       /boot           ext3    defaults        0       2
/dev/mapper/Ubuntu-swap_1 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

---

### Post by Cirrocco on 2006-03-05
I was thinking maybe this is just how GParted handles reiserfs /root partitions, can anyone verify this?

---

### Post by plors on 2006-03-05
use gparted on it's own [livecd]("http://gparted.sourceforge.net/livecd.php").

cheers :cool:

---

