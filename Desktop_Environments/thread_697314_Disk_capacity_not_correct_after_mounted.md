---
title: "Disk capacity not correct after mounted"
date: 2008-02-15
forum: Desktop Environments
---

### Post by leohart on 2008-02-15
I have problems with getting my mount to show its full capacity. As you can see below, my device (linear RAID) has 2TB of space. However, after mounting, running dh -f, it only shows the capacity of 1 drive in the RAID. What can I do to fix this? Any suggestion is welcomed

Running fdisk -l (irrelevant entries truncated)

```
Disk /dev/sdd: 1124.9 GB, 1124999233536 bytes
255 heads, 63 sectors/track, 136773 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      136773  1098629091   83  Linux

Disk /dev/sde: 1124.9 GB, 1124999233536 bytes
255 heads, 63 sectors/track, 136773 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      136773  1098629091   83  Linux

Disk /dev/md3: 2249.9 GB, 2249992175616 bytes
2 heads, 4 sectors/track, 549314496 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md3 doesn't contain a valid partition table
```

Running mdadm -Ds /dev/md3

```
/dev/md3:
        Version : 00.90.01
  Creation Time : Mon Aug 27 17:22:51 2007
     Raid Level : linear
     Array Size : 2197257984 (2095.47 GiB 2249.99 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 3
    Persistence : Superblock is persistent

    Update Time : Thu Sep 27 17:16:08 2007
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

       Rounding : 64K

           UUID : 509b4562:b6f2917d:43e383c9:83b5f043
         Events : 0.5

    Number   Major   Minor   RaidDevice State
       0       8       49        0      active sync   /dev/sdd1
       1       8       65        1      active sync   /dev/sde1
```

However, after mounting, running df -h, the capacity is shown incorrectly.

```
/dev/md3              1.1T  979G   11M 100% /home/extras
```

---

