---
title: "Booting Error!!!"
date: 2009-04-03
forum: General Help
---

### Post by letmekilluplz on 2009-04-03
I had ubuntu and Vista and tried to install XP and when I did It boots straight into Vista. I took off the XP partition and it still goes straight to vista. I know I still have ubuntu because all my files are still on the partition its just a matter of bringing back the boot screen help please!

---

### Post by kevstar31 on 2009-04-03
pop in the ubuntu install disk open up a terminal and post the output of *fdisk -l*

---

### Post by letmekilluplz on 2009-04-03
Will do hold on...

---

### Post by letmekilluplz on 2009-04-03
fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by letmekilluplz on 2009-04-04
Well it's been twelve hours... Bump

---

### Post by Peter09 on 2009-04-04
Hi - are you sure you typed fdisk -l(for list) not 1 or i. The message you have suggests that you did not type the command correctly.

---

### Post by letmekilluplz on 2009-04-04
fdisk -l
Cannot open /dev/sda
Cannot open /dev/sdb


Thats fdisk -l (L)

---

### Post by Peter09 on 2009-04-05
Oh the full command is


```
sudo fdisk -l
```

---

### Post by letmekilluplz on 2009-04-05
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00b00485

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  27  Unknown
/dev/sda2   *        1275       10383    73168042+   6  FAT16
/dev/sda3           10384       19457    72886905   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ea9be

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

---

### Post by letmekilluplz on 2009-04-05
I just read that if you install Windows after Ubuntu it destroys the bootloader Im pretty sure that is what happened is there anyway to fix it?

---

### Post by Peter09 on 2009-04-06
Try

[http://www.smokinglinux.com/tutorials/restore-grub-boot-loader-in-your-ubuntu-linux](http://www.smokinglinux.com/tutorials/restore-grub-boot-loader-in-your-ubuntu-linux)

---

### Post by letmekilluplz on 2009-04-06
Solved thanks

---

