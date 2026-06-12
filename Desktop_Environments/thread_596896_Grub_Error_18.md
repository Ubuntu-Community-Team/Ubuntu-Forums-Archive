---
title: "Grub Error 18"
date: 2007-10-30
forum: Desktop Environments
---

### Post by amileaway on 2007-10-30
I am getting error 18 and 17.

I have 320gb Sata drive. vista installed and 40gb sec, ubuntu installed. Installation went fine and then when I started I got error 18. I read articles and one of them was referring to  add /boot partition and then I get error 17. I don't know what the deal is. 

Here is what I get when I boot up with live cd with fdisk command. 

sk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x39fc380c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         662     5314560   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         662       38914   307254272    7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9fbb9fbb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          62      497983+  82  Linux swap / Solaris
/dev/sdb2              63         186      996030   83  Linux
/dev/sdb3             187        4865    37584067+  83  Linux

Normally error 18 is for BIOS problem that does not support large capacity drives. But thats not the case here  or im missing something. Can somebody help me out ? If I need to modify grub how can i do it by booting from live cd?

---

### Post by logos34 on 2007-10-30
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)

To edit grub files from live cd:

Places>computer

click on root partition to mount 

open terminal and type:

**gksudo gedit /media/disk/boot/grub/menu.lst**

---

