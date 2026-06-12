---
title: "Where can i see..."
date: 2006-07-10
forum: Desktop Environments
---

### Post by Somenoob on 2006-07-10
if my system supports DMA?

---

### Post by halfvolle melk on 2006-07-10
Do you have a SATA disk? If so, does it show up as sda/sdb/sd*? In that case it's already using DMA.

And otherwise, if you've got IDE disks, "hdparm /dev/dh*" should return something like "using_dma = 1 (on)".

---

