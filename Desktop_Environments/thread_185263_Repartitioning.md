---
title: "Repartitioning ?"
date: 2006-05-31
forum: Desktop Environments
---

### Post by interse on 2006-05-31
Before I upgrade to 6.06, I would like to repartition my hard drive.  Currently it is partitioned as follows:
      hda1   ext 3    36735 MB     13397 MB   Used     23338 Unused
      hda 2  extended    1428
            hda 5  linux-swap   1428

I would like to create a /home partition for data.   Using GParted LIVE, would I be able to resize  hda1 and create   hda3   (around 18000 MB) from the space created by resizing.    Could this be done safely.     I would prefer to take this approach rather than reformatting the whole drive.

---

### Post by carlosqueso on 2006-05-31
In theory yes, although it has refused to do it for me.  Just don't delete any partitions and you should be fine.

---

### Post by aysiu on 2006-05-31
Follow these instructions:
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

---

