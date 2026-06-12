---
title: "Raid 10 issues"
date: 2009-05-27
forum: General Help
---

### Post by slmagus on 2009-05-27
So I have a backup server running backuppc software to do all my backups. The disk in the machine are configured in a raid 10 array.

/dev/sda - 500 G
/dev/sdb - 400 G
/dev/sdc - 500 G
/dev/sdd - 400 G

> # /dev/md0 level=raid1 num-devices=2 UUID=48487d2c:f9b59d98:a1ef81c3:5299d396

ARRAY /dev/md1 level=raid10 num-devices=4 devices=/dev/sda2,/dev/sdb1,/dev/sdc2,/dev/sdd1

The fourth disk failed recently, so I put in a new disk formatted it, and re-added it to the array.

After the array finishes re syncing it. I soon get a degraded array event email stating the disk has been failed from the array.

If I try to access the disk it says it dosen't exsist or is unavailable sometimes a reboot will fix it. I've tried three disks now, all of which should be working.

Sometimes a reboot will fix its detection, sometimes not.
```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid10 sda2[0] sdc2[2] sdb1[1]
      781417472 blocks 64K chunks 2 near-copies [4/3] [UUU_]

md0 : active raid1 sda1[0] sdc1[1]
      97659008 blocks [2/2] [UU]

unused devices: <none>
```

---

### Post by fjgaude on 2009-05-27
What does this show:

```
sudo mdadm -D /dev/md1
```

Let us know.

---

### Post by slmagus on 2009-05-27
```
/dev/md1:
        Version : 00.90.03
  Creation Time : Thu Mar  5 11:36:26 2009
     Raid Level : raid10
     Array Size : 781417472 (745.22 GiB 800.17 GB)
  Used Dev Size : 390708736 (372.61 GiB 400.09 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Wed May 27 10:20:27 2009
          State : clean, degraded
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : near=2, far=1
     Chunk Size : 64K

           UUID : 3b3499f8:e64dcd55:c91d1289:ceb97d9c (local to host backup)
         Events : 0.85136

    Number   Major   Minor   RaidDevice State
       0       8        2        0      active sync   /dev/sda2
       1       8       17        1      active sync   /dev/sdb1
       2       8       34        2      active sync   /dev/sdc2
       3       0        0        3      removed

```

---

### Post by slmagus on 2009-05-27
I may have been swapping out the wrong disk the entire time, so I swapped out a different disk and will try that now. It got confusing because the /dev/sdX didn't necessarily match up to what the order that they were plugged into the motherboard.

---

### Post by fjgaude on 2009-05-28
Well, keep at it and you will learn what's necessary to get the array fully up.

---

