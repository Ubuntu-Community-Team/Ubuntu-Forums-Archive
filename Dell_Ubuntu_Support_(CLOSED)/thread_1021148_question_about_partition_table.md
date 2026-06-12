---
title: "question about partition table"
date: 2008-12-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by woodside on 2008-12-25
I have a question about how Dell set up the partition on my system which was preinstalled with Ubuntu. The table is as follows:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8         399     3148740    b  W95 FAT32
/dev/sda3   *         400       30143   238918680   83  Linux
/dev/sda4           30144       30394     2016157+   5  Extended
/dev/sda5           30144       30394     2016126   82  Linux swap / Solaris
```

I would like to add a few more partitions to try out other distros. I understand sda3 is where Ubuntu lives and sda5 is the swap, but what are sda1, sda2 and sda4...Dell Utility, W95 FAT32 and Extended and, more importantly, should I leave them alone?

---

### Post by armandh on 2008-12-25
sda4 is the extended partition that containd the swap partition.
sda2 may have been [is?] a win 95 os

I would suggest a live partition utility such as parted magic.
the gui is easier [for me]
it shows the partitions and how full they are
the option to shrink delete move etc are easier to visualize.

the easiest way to test install other OS is with a different HDD
instead of your working one. you can't screw up what is disconected.

---

### Post by gbrainin on 2008-12-25
The default partitioning is explained in the Dell Linux Wiki: [http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Default_Partitions]("http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Default_Partitions")

---

### Post by woodside on 2008-12-25
thanks for the advice guys...it's a good starting point and I'll do some more research on this.

---

