---
title: "GX-260 Install issues"
date: 2011-01-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ErroneousRex on 2011-01-26
Hey guys/gals,
I've been searching this forum for the past couple of days now and have been trying some advice given to similar situations, but have not been successful yet. So I decided to make an account to see if some one may be nice enough to offer up some advice :)

OK, so I have a Dell GX-260 (old as dirt) with two hard drives. I just DBAN'ed them because I have uninstalled/reinstalled windows XP and Ubuntu too many times. So Im starting fresh.

I installed Ubuntu 10.10 by itself, I will worry about XP later, and it fails to boot. I have used the live cd to try to run sudo update-grub and the following error is returned:
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

but os-prober returns:
/dev/sda1:Ubuntu 10.10 (10.10):Ubuntu:linux

and fdisk -l returns:
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dae8c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9630    77346816   83  Linux
/dev/sda2            9630       10012     3068929    5  Extended
/dev/sda5            9630       10012     3068928   82  Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

so I know that the system is installed and it seems like it should boot but it just doesn't. I believe the problem lies in grub2.

If anyone can help me out that would be awesome and I would be forever grateful!

Oh and I have attached the results.txt file of boot_script

---

### Post by ErroneousRex on 2011-01-26
previously the only install that produced a working dual boot was a WUBI 10.04 install.

---

### Post by ErroneousRex on 2011-01-26
Any ideas?

---

### Post by ErroneousRex on 2011-01-26
Bump

---

