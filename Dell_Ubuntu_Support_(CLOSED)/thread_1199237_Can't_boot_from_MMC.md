---
title: "Can't boot from MMC"
date: 2009-06-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by berlichman on 2009-06-28
Trying to dual boot from 16 GByte MMC on a Dell Mini 9 under Ubuntu 9.04.  GParted (version 0.4.5) shows MMC and I've changed flag to "boot".  Fdisk also shows the MMC:

*********************
bruce@bruce-netbook:~$ sudo fdisk -l
[sudo] password for bruce: 

Disk /dev/sda: 7682 MB, 7682605056 bytes
255 heads, 63 sectors/track, 934 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeebce539

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1         934     7502323+   5  Extended
/dev/sda5               1         912     7325577   83  Linux
/dev/sda6             913         934      176683+  82  Linux swap / Solaris

Disk /dev/mmcblk0: 16.1 GB, 16135487488 bytes
255 heads, 63 sectors/track, 1961 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007dc1e

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1   *           1        1961    15751701   83  Linux

Disk /dev/sdb: 4059 MB, 4059561984 bytes
255 heads, 63 sectors/track, 493 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x006a0e92

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         494     3964384+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(492, 254, 63) logical=(493, 139, 30)

*********************bruce@bruce-netbook:/boot/grub$ more menu.lst
default		0
timeout		5
color cyan/blue white/blue

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		88fe023c-e1ac-4e15-9134-7ec9f42c7939
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=88fe023c-e1ac-4e15-913
4-7ec9f42c7939 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

Would appreciate any help.  Thanks.

Bruce

---

### Post by jeremymcclure on 2009-06-28
The dell mini 9's bios does not allow it to boot off of the SD slot.  It does on the other hand allow for booting from a SD Reader in an available USB slot.


annoying i know

---

### Post by berlichman on 2009-06-29
damn!

---

