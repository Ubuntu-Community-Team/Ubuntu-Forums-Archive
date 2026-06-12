---
title: "Strange mdadm Raid 1 Problem"
date: 2009-01-05
forum: General Help
---

### Post by jleezer on 2009-01-05
Hello All.
I had a software raid 1 setup with two sata drives (sdb1 and sdc1) that were partitioned with ext3. The raid was at md0 and had a ext3 partition. Now through a strange series of events, the md0 ext3 partition was deleted and gparted reports it as unallocated space. However, it is still mounted and I am still able to read all the data that was on it and write to it. I was wondering if this is a problem? Is there anyway to add a repartition to md0 without erasing the data on the two drives? Is it even needed? Thanks for all the help, I'm kinda new at this so forgive me if this is a weird question.

---

### Post by fjgaude on 2009-01-06
Well, all we know says that **GParted** doesn't understand raid arrays. You can run **mdadm** to show the health of your array:

```
sudo mdadm -D /dev/md0
```

That will give lots health info.

Let us know how you are doing.

---

### Post by Coreigh on 2009-01-06
I agree with fjgaude, you can not use gparted to manage a software RAID volume. *HARDWARE* may be a different story.

here is a link that disusses software RAID on Linux using mdadm tools:
[http://nst.sourceforge.net/nst/docs/user/ch14.html](http://nst.sourceforge.net/nst/docs/user/ch14.html)

---

### Post by jleezer on 2009-01-06
Thanks a lot for the advice. Here is the result of mdadm -D /dev/md0:

/dev/md0:
        Version : 00.90.03
  Creation Time : Mon Dec 29 17:37:57 2008
     Raid Level : raid1
     Array Size : 625129216 (596.17 GiB 640.13 GB)
  Used Dev Size : 625129216 (596.17 GiB 640.13 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Jan  6 14:19:10 2009
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

          Events : 0.16

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1

From what I can tell all seems well to me. Thanks again.

---

### Post by fjgaude on 2009-01-06
You are good to go. Let us know if you have any other issues.

---

