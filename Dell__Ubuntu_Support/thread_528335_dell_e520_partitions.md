---
title: "dell e520 partitions"
date: 2007-08-17
forum: Dell  Ubuntu Support
---

### Post by jacob01 on 2007-08-17
i was looking around and i saw how people had a standard hard drive with 3 partition so i ran     sudo fdisk -l and got this 

jacob@dell:~$ sudo fdisk -l
Password:

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6         267     2104515    b  W95 FAT32
/dev/sda3   *         268         292      200812+  83  Linux
/dev/sda4             293       30394   241794315    f  W95 Ext'd (LBA)
/dev/sda5             293         452     1285168+  82  Linux swap / Solaris
/dev/sda6             453       30394   240509083+  83  Linux
jacob@dell:~$ 

wow this is the amount of partitions that are loaded on a dell e520n with 250 gig hard drive


what are these for i know that sda1 is a dell utility (why did they put this on my drive?) the sda3 is the file system because it is bootable  and sda5 is the swap

but what are the others?

---

### Post by jacob01 on 2007-08-18
bump

---

### Post by jb201116 on 2007-09-11
> **jacob01 said:**
> i was looking around and i saw how people had a standard hard drive with 3 partition so i ran     sudo fdisk -l and got this 

jacob@dell:~$ sudo fdisk -l
Password:

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6         267     2104515    b  W95 FAT32
/dev/sda3   *         268         292      200812+  83  Linux
/dev/sda4             293       30394   241794315    f  W95 Ext'd (LBA)
/dev/sda5             293         452     1285168+  82  Linux swap / Solaris
/dev/sda6             453       30394   240509083+  83  Linux
jacob@dell:~$ 

wow this is the amount of partitions that are loaded on a dell e520n with 250 gig hard drive


what are these for i know that sda1 is a dell utility (why did they put this on my drive?) the sda3 is the file system because it is bootable  and sda5 is the swap

but what are the others?

Ok  here goes...

sda1 is probably where they put the base windows install or drivers given the size of the partition
sda2 and sda4 are Windows95 partitions (how old is your system??)
sda3 is the standard linux boot partion (root)
sda5 is the swap space ( temporary space for core dumps etc)
sda6 is your main linux space for your filesystem

its something like that anyway from what I can see.

You could try running fstab in a terminal and it would give you a better idea of what's what

Hope this helps
jb201116

---

