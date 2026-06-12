---
title: "resize partitions on raid drives?"
date: 2009-02-05
forum: General Help
---

### Post by eppo on 2009-02-05
when i first installed my server i had 5 500 gig drives, i put the install on a partition (might have been 40gigs) and used the rest for a raid5. after some trouble, i reinstalled and put the os on its own drive. as far as i can tell, each drive is not using the full 500 gigs, each one is using 465.76. here is a copy of mdadm -D /dev/md0:
/dev/md0:
        Version : 00.90
  Creation Time : Sun Sep  7 14:39:47 2008
     Raid Level : raid5
     Array Size : 1953535744 (1863.04 GiB 2000.42 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Feb  5 05:41:37 2009
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 69a2ea09:b978d90b:9c682ae7:cd63b594
         Events : 0.917920

    Number   Major   Minor   RaidDevice State
       0       8       65        0      active sync   /dev/sde1
       1       8        1        1      active sync   /dev/sda1
       2       8       17        2      active sync   /dev/sdb1
       3       8       33        3      active sync   /dev/sdc1
       4       8       49        4      active sync   /dev/sdd1

any way to get the raid to use that extra space on each drive? and use the full 500 gigs from each drive?
thanks

---

### Post by geirha on 2009-02-05
500 GB == 465.7 GiB. You are using all of the drives.

[http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)

---

### Post by eppo on 2009-02-05
thought that i might have, because the last time my drive died, i replaced the bad drive and did mdadm --grow, and the raid drive size did increase.
thanks for the info.

---

