---
title: "Grub is giving an error 13 when i try to boot windows."
date: 2009-03-05
forum: General Help
---

### Post by linux noooob on 2009-03-05
I re formated and installed windows but ever since I moved it around on the partition table to the front of the drive it has this weird error! 

menu.lst:

```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		f235a127-22b4-42ab-81e7-5d247bb1c1c8
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=f235a127-22b4-42ab-81e7-5d247bb1c1c8 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		f235a127-22b4-42ab-81e7-5d247bb1c1c8
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=f235a127-22b4-42ab-81e7-5d247bb1c1c8 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		f235a127-22b4-42ab-81e7-5d247bb1c1c8
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f235a127-22b4-42ab-81e7-5d247bb1c1c8 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		f235a127-22b4-42ab-81e7-5d247bb1c1c8
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f235a127-22b4-42ab-81e7-5d247bb1c1c8 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		f235a127-22b4-42ab-81e7-5d247bb1c1c8
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
rootnoverify		(hd0,3)
savedefault
makeactive
chainloader	+1

```

My boot.ini
```
[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect

```

and what fdisk returns:
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x43c2efb5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12946   103988713+   c  W95 FAT32 (LBA)
/dev/sda3           12947       14518    12627090   83  Linux
/dev/sda4   *       14519       14593      602437+  82  Linux swap / Solaris

```


I also re installed grub from a live CD

---

### Post by meierfra. on 2009-03-14
(hd0,3) is your swap partition.  Your windows partition seems to be "/dev/sda1"  (Why did you install XP on a Fat partition?)

Use:


title		Microsoft Windows XP Home Edition
rootnoverify   (hd0,0)
chainloader	+1

---

### Post by Krokofant on 2009-03-17
I have the same problem. I get Grub Error 13: "Invalid or unsupported executable format" wenn I try to boot Windows. The problem occurred after reinstalling Kubuntu.

fdisk -l

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x86222fd5                     

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00005c2c                     

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sdb2           12749       29647   135741217+  83  Linux    
/dev/sdb3           29648       30401     6056505   82  Linux swap / Solaris

Disk /dev/sdc: 250.0 GB, 250059350016 bytes                                                                                                    
255 heads, 63 sectors/track, 30401 cylinders                                                                                                   
Units = cylinders of 16065 * 512 = 8225280 bytes                                                                                               
Disk identifier: 0x38577ca9                                                                                                                    
                                                                                                                                               
   Device Boot      Start         End      Blocks   Id  System                                                                                 
/dev/sdc1   *           1       30401   244196001   83  Linux                                                                                  
                                                                                                                                               
Disk /dev/sdd: 400.0 GB, 400088457216 bytes                                                                                                    
255 heads, 63 sectors/track, 48641 cylinders                                                                                                   
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02864087

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       48641   390708801    7  HPFS/NTFS
```

/root/grub/menu.lst

```
title           Ubuntu 8.10, kernel 2.6.27-11-generic
uuid            870609f7-f4f9-471c-8e02-5a28e8bb245c
kernel          /boot/vmlinuz-2.6.27-11-generic root=UUID=870609f7-f4f9-471c-8e02-5a28e8bb245c ro quiet splash
initrd          /boot/initrd.img-2.6.27-11-generic
quiet

title           Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid            870609f7-f4f9-471c-8e02-5a28e8bb245c
kernel          /boot/vmlinuz-2.6.27-11-generic root=UUID=870609f7-f4f9-471c-8e02-5a28e8bb245c ro  single
initrd          /boot/initrd.img-2.6.27-11-generic

title           Ubuntu 8.10, kernel 2.6.27-7-generic
uuid            870609f7-f4f9-471c-8e02-5a28e8bb245c
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=870609f7-f4f9-471c-8e02-5a28e8bb245c ro quiet splash
initrd          /boot/initrd.img-2.6.27-7-generic
quiet

title           Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid            870609f7-f4f9-471c-8e02-5a28e8bb245c
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=870609f7-f4f9-471c-8e02-5a28e8bb245c ro  single
initrd          /boot/initrd.img-2.6.27-7-generic

title           Ubuntu 8.10, memtest86+
uuid            870609f7-f4f9-471c-8e02-5a28e8bb245c
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Windows XP Professional x64 Edition
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1
```

I hope someone can help.

---

### Post by meierfra. on 2009-03-17
Krokofant:

Add these three items to menu.lst

title           Windows XP Professional x64 Edition (hd0)
root            (hd0,0)
chainloader     +1

title           Windows XP Professional x64 Edition (hd2)
root            (hd2,0)
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +1

title           Windows XP Professional x64 Edition (hd3)
root            (hd3,0)
map             (hd0) (hd3)
map             (hd3) (hd0)
chainloader     +1


Reboot, try the different titles in the Grub Menu, until you find one which works.  You can  then delete all the others from menu.lst.

If none of them works, report all the error messages you got.


P.S  For future problems, please start you own threads. Trying to solve more than one problem in a  thread can get pretty confusing.

---

### Post by ruel- on 2009-03-17
problem already been solved here:

[http://ubuntuforums.org/showthread.php?t=282545](http://ubuntuforums.org/showthread.php?t=282545)

---

