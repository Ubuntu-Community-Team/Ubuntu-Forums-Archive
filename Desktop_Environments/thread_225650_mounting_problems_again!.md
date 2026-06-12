---
title: "mounting problems again!?"
date: 2006-07-30
forum: Desktop Environments
---

### Post by Nikku49 on 2006-07-30
ok, here is my problem, i installed fuse, and ntfs-3g to try to get write access to my ntfs drives, well after i installed fuse,ntfs-3g i couldnt mount the drives. i keep getting an error telling me my mount point is already mounted or my drives are busy. so i remove fuse from /etc/modules and set my fstab back to original and now i still cant mount the drives. :confused: i keep getting the same error. any ideas? here is my fstab 

[FONT="Arial"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0   1      /dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1       /media/hdb      ntfs    nls=utf8,umask=0222 0    0
/dev/hdf1       /media/hdf      ntfs    nls=utf8,umask=0222 0    0[/FONT]

---

### Post by Nikku49 on 2006-07-30
kk i fixed teh problem, apperently i had my ntfs drives mounted when my system crashed. and i guess it left the drives open or unlocked i unno, but i fixed it by popping in a winxp disc and went through the installer untill it asked me what partition i wanted to use. then i rebooted into ubuntu and bam i can mount my drives again :)

---

