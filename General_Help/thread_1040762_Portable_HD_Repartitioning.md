---
title: "Portable HD Repartitioning"
date: 2009-01-15
forum: General Help
---

### Post by GolemdX on 2009-01-15
Anyways, I had ubuntu 8.10 installed on a 250GB Western Digital external hard drive. I borrowed a GParted Live CD from a friend, and resized the ubuntu partition and added an NTFS partition to the right of it, to the left of the swap space. Well, when I went to the boot menu, I could no longer boot to GRUB on the drive. How can I make my drive bootable again?

---

### Post by skern03 on 2009-01-15
> **GolemdX said:**
> Anyways, I had ubuntu 8.10 installed on a 250GB Western Digital external hard drive. I borrowed a GParted Live CD from a friend, and resized the ubuntu partition and added an NTFS partition to the right of it, to the left of the swap space. Well, when I went to the boot menu, I could no longer boot to GRUB on the drive. How can I make my drive bootable again?

From GParted, select the external drive. From the menu, choose Partition, Manage Flags (see attached screen shot). The first option in the dialog window is boot. Click it. That should make the partition bootable.

If that's not the problem, then you may have to reconfigure GRUB. There are a lot of threads on that in this forum.

---

### Post by GolemdX on 2009-01-17
Thanks, I'll try it as soon as GParted finishes downloading/burning.

---

