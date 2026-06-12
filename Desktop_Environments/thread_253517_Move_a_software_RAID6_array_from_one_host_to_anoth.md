---
title: "Move a software RAID6 array from one host to another?"
date: 2006-09-08
forum: Desktop Environments
---

### Post by millerdc on 2006-09-08
What is the most painless way to migrate a software RAID6 array from one host to another? Can I use the /proc/mdstat output to create an mdadm.conf file? I'm not clear on the exact command to give to assemble the RAID. All the disks in the array are in one house that uses firewire as the interface. Here is what my mdstat shows.

Personalities : [raid6] 
md0 : active raid6 sda2[0] sdd2[5] sdc2[4] sdf2[3] sde2[2] sdb2[1]
      980468992 blocks level 6, 64k chunk, algorithm 2 [6/6] [UUUUUU]
      
unused devices: <none>


Here is the output from mdadm --detail

/dev/md0:
        Version : 00.90.03
  Creation Time : Sun Aug 27 16:59:20 2006
     Raid Level : raid6
     Array Size : 980468992 (935.05 GiB 1004.00 GB)
    Device Size : 245117248 (233.76 GiB 251.00 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Sep  8 10:25:38 2006
          State : clean
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

           UUID : 8edda9da:bad9bef1:05cdf7a2:47ee9552
         Events : 0.127364

    Number   Major   Minor   RaidDevice State
       0       8        2        0      active sync   /dev/sda2
       1       8       18        1      active sync   /dev/sdb2
       2       8       66        2      active sync   /dev/sde2
       3       8       82        3      active sync   /dev/sdf2
       4       8       34        4      active sync   /dev/sdc2
       5       8       50        5      active sync   /dev/sdd2

---

### Post by millerdc on 2006-12-21
I just thought I would bump this back up to see if anyone out there could help me out. The array and the host are doing fine but I would still like to know the proper way of doing this. Thanks.

---

