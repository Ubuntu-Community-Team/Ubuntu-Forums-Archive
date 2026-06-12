---
title: "AVAILABLE space in inferior to FREE space on hd"
date: 2009-11-13
forum: Desktop Environments
---

### Post by manolomanolo on 2009-11-13
Hi to all.

I'm logged as normal user. I can see an high difference between the AVAILABLE and the FREE space on the partitions of my hard drive, as shown in the following screenshot:

[IMG]http://img43.imageshack.us/img43/1060/screenshotsystemmonitora.png[/IMG]

Actually I've been able to recover some space removing files I've been trashing as root: so I run
```
sudo nautilus
```

and then removed the files in some ".trash" directory. is there any other way to reduce the difference between AVAILABLE and FREE space?

Thanks.

Ubuntu 9.10 - Karmic Koala
```
uname -r
2.6.31-14-generic

```

---

### Post by scorp123 on 2009-11-13
5% are always reserved for super-user "root". Problem solved :)

---

### Post by manolomanolo on 2009-11-13
Subtracting the 5% of 3.1 GB, would leave 2.945 GB of available space root on partition. On the other hand, subtracting the 5% of 1.4 GB would leave 1.330 GB on home partition.
While in my case, respectively 2.6 GB and 858.9 MB (in this last case it's quite the 50%!!!) are left.

So, the problem is not solved.:confused:

---

### Post by ogcub on 2009-11-13
5% of partition size is reserved, not 5% of free space, that way you could always have no free space and no reserved space. You can change reserved percentage using tune2fs, however it's not recommended, especially for system partition

---

### Post by manolomanolo on 2009-11-13
Ah, ok! Now it's clear ;). So everything is ok.

Thank you!

---

