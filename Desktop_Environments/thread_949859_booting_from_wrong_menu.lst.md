---
title: "booting from wrong menu.lst"
date: 2008-10-16
forum: Desktop Environments
---

### Post by dancer58 on 2008-10-16
I installed a new disk and installed Intrepid on the first partition. When I boot both Hardy (on old disk)or Intrepid (on new disk) it always uses menu.lst on the Hardy install.
How do I change to use menu.lst in Intrepid ?

fdisk -l | grep Disk

Disk /dev/sda: 160.0 GB, 160041885696 bytes   ( XP ) sata
Disk identifier: 0x002c61a0

Disk /dev/sdb: 250.0 GB, 250059350016 bytes  ( Ubuntu Intrepid--new drive ) sata
Disk identifier: 0x00012393

Disk /dev/sdc: 81.9 GB, 81964302336 bytes    (Ubuntu Hardy--old drive ) pata
Disk identifier: 0xcd6b4724

=========================================================

Device map
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc

Thanks
Harold

---

