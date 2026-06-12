---
title: "RAID - Drive Died, Replaced, How do I rebuild?"
date: 2009-01-03
forum: General Help
---

### Post by Ngtstlkr on 2009-01-03
My second drive in my MDADM raid died, and I have replaced the drive.  I can't figure out how to add the second drive back in the array, and I am really scared about loosing the data in my first drive.  Here is some info:

If I run the MDADM --misc to get the information, I get the below:
```

john@ubuntu-01:~$ sudo mdadm --misc -D /dev/md0

/dev/md0:
        Version : 00.90.03
  Creation Time : Thu Oct 23 22:05:22 2008
     Raid Level : raid1
     Array Size : 976762496 (931.51 GiB 1000.20 GB)
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Jan  3 22:14:21 2009
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : 85d71553:f6bd28b4:a596020d:c5186086 (local to host ubuntu-01)
         Events : 0.2363272

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       0        0        1      removed

```

My drives in the raid are /dev/sdb and /dev/sdc.  How do I get /dev/sdc back in the array and rebuild it without losing data on my /dev/sdb??

---

### Post by srt4play on 2009-01-03
```
sudo mdadm --add /dev/md0 /dev/sdc
```

should kick off the resync, watch the progress with

```
watch cat /proc/mdstat
```

---

### Post by Ngtstlkr on 2009-01-04
That did the trick in every way, plus being able to monitor helped a lot!  Thanks, really appreciate it. :)

---

