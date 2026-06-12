---
title: "mdadm raid 1 problem"
date: 2009-01-30
forum: General Help
---

### Post by oiad on 2009-01-30
I have a raid 1 setup with mdadm on my system that has been working perfectly.  On the 2 drives there are a couple of different partitions raided together, and after a power problem yesterday the array with my file system on it (md0) will not load.  
   I see the ubuntu splash screen, but then I just receive a message that /dev/md0 doesn't exist. I booted the live cd, and after installing mdadm the other array on these hard drives works fine.  When I checked mdadm.conf it showed the uuid for the array but it has 'spares=2' following it, implying that both of the drives are spares.  When I examine the drives with mdadm I have some strange results on how many drives it states that there are.  Any help getting this system bootable would be greatly appreciated.

```
 sudo mdadm --examine /dev/sd[ab]1
/dev/sda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 1d979f1b:f1aaa0c4:2220fe66:5deb2dae
  Creation Time : Sun Dec 28 22:50:08 2008
     Raid Level : raid1
  Used Dev Size : 24410624 (23.28 GiB 25.00 GB)
     Array Size : 24410624 (23.28 GiB 25.00 GB)
   Raid Devices : 2
  Total Devices : 4
Preferred Minor : 0

    Update Time : Thu Jan 29 03:48:43 2009
          State : active
 Active Devices : 2
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 879bd42b - correct
         Events : 9


      Number   Major   Minor   RaidDevice State
this     0       0        0        0      spare

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 1d979f1b:f1aaa0c4:2220fe66:5deb2dae
  Creation Time : Sun Dec 28 22:50:08 2008
     Raid Level : raid1
  Used Dev Size : 24410624 (23.28 GiB 25.00 GB)
     Array Size : 24410624 (23.28 GiB 25.00 GB)
   Raid Devices : 2
  Total Devices : 13
Preferred Minor : 0

    Update Time : Thu Jan 29 03:48:43 2009
          State : active
 Active Devices : 7
Working Devices : 7
 Failed Devices : 6
  Spare Devices : 0
       Checksum : 438835d4 - correct
         Events : 9


      Number   Major   Minor   RaidDevice State
this 2005487419   1503392883    1233711139    -1857218597      faulty write-mostly

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1

```

---

### Post by oiad on 2009-01-31
Well I didn't have the time to wait to figure this out, so I just backed up my data and reinstalled.  Sorry for the next person.

---

