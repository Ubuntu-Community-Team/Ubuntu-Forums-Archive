---
title: "[XFCE] a 1K volume showing up at my desktop"
date: 2007-10-31
forum: Desktop Environments
---

### Post by fifafrazer on 2007-10-31
When I boot into my Xubuntu 7.10 system, there's a device showing op at my desktop called "1 K Volume". When I try to mount it, it fails with "unable to determine mount point for /dev/sda2". The problem is that the device doesn't exist, but it shows up on my desktop. 

When starting GParted it will scan for drives for about 5 minutes at 100 % CPU load, and then it shows my partitions as it is supposed to, and there's no "1 K volume", and the icon automatically disappears from my desktop. As you can see on my attached screenshot, /dev/sda2 is an extended partition.


Here's my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=acb69049-e837-403d-a26c-95f4c0d08003 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdc5
UUID=f9f03141-c59c-42c8-9cff-07f1c2181550 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

/dev/sda1	/mnt/winC	ntfs-3g		rw,user,auto,exec,umask=0
/dev/sda5	/mnt/winD	ntfs-3g		rw,user,auto,exec,umask=0
/dev/sdb1	/mnt/winH	ntfs-3g		rw,user,auto,exec,umask=0 
```

Actually I have a second problem as well. After a reboot, the ntfs-3g processes sometimes use 100% cpu time and a lot of memory for some minutes. After some time, there's no problems. Could it be caused by my almost full ntfs partitions (5-10 % free space)

---

### Post by fifafrazer on 2008-01-06
The NTFS-3G was caused by full HDD, but I still haven't find the solution for the other issue.  Still noone can help?

---

