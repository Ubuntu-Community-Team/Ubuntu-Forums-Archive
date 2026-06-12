---
title: "No Windows in Boot Menu"
date: 2009-03-06
forum: General Help
---

### Post by Core2duo on 2009-03-06
I have recently installed linux - ubuntu into my hdd partinion which belonged to windows under letter c (i have other windows under letter f) and there is partinion d which only stores files. The problem is, that after installation, I get a new table which lets me choose what to boot, but there is no xp there. Original file looks like:

default 0
timeout 3

title Ubuntu 8.10, kernel 2.6.27-11-generic
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=3d1cdd72-0e80-47e9-9281-d344b804ea2f ro quiet splash
initrd /boot/initrd.img-2.6.27-11-generic

title Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=3d1cdd72-0e80-47e9-9281-d344b804ea2f ro  single
initrd /boot/initrd.img-2.6.27-11-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=3d1cdd72-0e80-47e9-9281-d344b804ea2f ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=3d1cdd72-0e80-47e9-9281-d344b804ea2f ro  single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
kernel /boot/memtest86+.bin

I tried many other cofigurations found on the internet. I also searched for ways to solve this problem, but none of it helped. Does anyone know what I should do to solve this problem?

---

### Post by wolfen69 on 2009-03-06
post the output of:
```
sudo fdisk -l
```

---

### Post by Core2duo on 2009-03-06
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfdedfded

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1       37607   302078196    5  Extended
/dev/sda3   *       37608       38913    10490442+   7  HPFS/NTFS
/dev/sda5            5723       37607   256116229    7  HPFS/NTFS
/dev/sda6               1        2432    19534945+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdd: 522 MB, 522043904 bytes
16 heads, 63 sectors/track, 1011 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x9b19e2c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        1010      509008+   6  FAT16

---

### Post by Core2duo on 2009-03-06
How fast this thread was moved to second page.

---

### Post by Core2duo on 2009-03-06
Please write me a solution.

---

