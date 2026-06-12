---
title: "Moving Ubuntu to a new disk"
date: 2009-02-20
forum: General Help
---

### Post by Lachlanus on 2009-02-20
When I first installed Ubuntu, I wasn't aware that I could modify the Windows XP partition already on the disk.  So I put in a 10GB hdd and put Ubuntu on that.  Well, I think the disk is too small, so I would like to clone it to my larger 160GB drive (the one with the Windows Partition).  I used GParted to shrink the WinXP partition and create a new ext3 partition on it, and flagged it as boot.  I used gddrescue to clone the original Ubuntu installation to the new partition.  When I remove the 10GB drive, the 160GB drive just boots to the WinXP partition, without going to the Dual boot menu.  What do I need to do to get the new Ubuntu partition booting?

---

