---
title: "How to repair fstab robustly?"
date: 2008-04-17
forum: Desktop Environments
---

### Post by lapwing on 2008-04-17
Hi,

I came from gentoo and hence I was used to editing configuration files etc by hand (looking at my previous post you can see how that got solved...). Anyways, now I am without swap. I have had this problem before, but now I would like to know how to solve it the ubuntu way.

I have got two drives (old ATA) and two swap partitions. One partition is /dev/sda5 and the other is /dev/sdb5. Previously, ATA partitions were called /dev/hd?? and hence my fstab is currently faulty. Easy fix: change h to s. However, if tomorrow developers decide to change the first letter again, I am booting without swap again! Is there a more robust way to changing fstab? So, that it will survive even changes in the partition table?

Thanks in advance!

---

