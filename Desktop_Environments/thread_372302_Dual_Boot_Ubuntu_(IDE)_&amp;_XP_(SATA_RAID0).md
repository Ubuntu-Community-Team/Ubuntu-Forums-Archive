---
title: "Dual Boot Ubuntu (IDE) &amp; XP (SATA RAID0)"
date: 2007-02-28
forum: Desktop Environments
---

### Post by matt8534 on 2007-02-28
I have xp installed on a software RAID0 and ubuntu installed on an IDE drive.  For some reason my BIOS will only boot from the IDE drive if it is connected (even though I have changed the drive boot order to the sata raid) so I am left w/ trying to get grub to boot into my xp installation.  I am having issues trying to get this going. 

windows section of grub.conf (as you can see I am using trial and error here to try to get this to work (none do), and have tried many other combos as well)

```
title Windows 1 (loader)
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
makeactive
chainloader +1

title Windows 2 (loader)
map (hd0,0) (hd2,0)
map (hd2,0) (hd0,0)
rootnoverify (hd2,0)
makeactive
chainloader +1

title Windows 3 (loader)
map (hd0,0) (hd3,0)
map (hd3,0) (hd0,0)
rootnoverify (hd3,0)
makeactive
chainloader +1
```

ubuntu section of grub.conf

```
title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hdd1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot
```

my device.map file

```
(fd0)   /dev/fd0
(hd0)   /dev/hdd
(hd1)   /dev/sda
(hd2)   /dev/sdb
```


Output from fdisk:

```
matt@ubuntu:/boot/grub$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       48641   390708801    7  HPFS/NTFS

Disk /dev/hdd: 30.7 GB, 30738677760 bytes
255 heads, 63 sectors/track, 3737 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        3581    28764351   83  Linux
/dev/hdd2            3582        3737     1253070    5  Extended
/dev/hdd5            3582        3737     1253038+  82  Linux swap / Solaris
matt@ubuntu:/boot/grub$
```


Any help in getting this resolved (rather than unplugging the power cable from my IDE drive) to get this thing to dual boot would be great!!

---

### Post by matt8534 on 2007-02-28
](*,) Any ideas fellas?????

---

