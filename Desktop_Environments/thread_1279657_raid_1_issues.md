---
title: "raid 1 issues"
date: 2009-10-01
forum: Desktop Environments
---

### Post by cezarica on 2009-10-01
Rebooted cos installed kernel 2.6.28-15-generic (via Update Manager) and now the raid 1 doesn't want to mount, yet worked fine before the reboot.
> 
**mdadm --detail /dev/md0**
/dev/md0:
        Version : 00.90
  Creation Time : Sun Sep 13 00:39:59 2009
     Raid Level : raid1
     Array Size : 390708736 (372.61 GiB 400.09 GB)
  Used Dev Size : 390708736 (372.61 GiB 400.09 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Oct  1 12:43:38 2009
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 1518549d:4ab05616:1fd2cba4:e8173d4a (local to host Delta)
         Events : 0.16

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1

> 
**cat /proc/mdstat **
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb1[0] sdc1[1]
      390708736 blocks [2/2] [UU]
      
unused devices: <none>


In /etc/fstab I got
> 
/dev/md0        /media/raid     ext2    defaults        0       0

and in /etc/mdadm/mdadm.conf
> 
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=1518549d:4ab05616:1fd2cba4:e8173d4a

I did a mount /media/raid (yes the mount /media/raid directory exists) and I get:
> 
**dmesg | tail**
[  378.777070] md: unbind<sdb1>
[  378.784018] md: export_rdev(sdb1)
[  378.784039] md: unbind<sdc1>
[  378.786156] md: export_rdev(sdc1)
[  386.662022] md: md0 stopped.
[  386.668538] md: bind<sdc1>
[  386.668668] md: bind<sdb1>
[  386.741470] raid1: raid set md0 active with 2 out of 2 mirrors
[  386.741594]  md0: unknown partition table
[  395.824420] VFS: Can't find an ext2 filesystem on dev md0.

I'm really desperate as I don't know what else to do and badly need to access some files that are on the raid. My boss is killing me...:(

edit:
got 1 HDD (on a partition is Ubuntu installed and got '/home' on the second) and 2 HDD that in raid 1 from bios and at **mdadm --examine --scan** I get:
> 
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=de878fb6:20f04d5f:1fd2cba4:e8173d4a
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=1518549d:4ab05616:1fd2cba4:e8173d4a

and don't get it why I get two arrays while only second array is assembled.

---

### Post by cezarica on 2009-10-01
Guess it's something with the new kernel version 2.6.28-15-generic, cos from Grub I started with the old one (version 2.6.28-11-generic) and the raid works smoothly. What should I do to make it work with the new one?

---

### Post by Lars Noodén on 2009-10-01
Try looking in /boot/grub/grub.cfg and comparing the parameters for the new kernel and the old kernel.

---

### Post by cezarica on 2009-10-02
I don't have /boot/grub/grub.cfg file. :confused:

---

### Post by cezarica on 2009-10-04
bump!

---

