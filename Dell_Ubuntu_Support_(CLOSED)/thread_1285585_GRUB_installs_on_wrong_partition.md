---
title: "GRUB installs on wrong partition?"
date: 2009-10-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jlbakker on 2009-10-07
Hello,
 
I installed 9.04 using the live CD. I have WinXP and 9.04 on the same disk, different partitions. WinXP is in sda3, linux in sda7. However, when I power up the PC, GRUB doesn't kick in. Instead, when I boot to the Dell Utility partition (using F2/F12, I assume /dev/sda1) GRUB kicks in but then gets stuck. I.e. I only see "GRUB" and nothing more.
 
How to configure my PC [DELL E510] such that when doing a power up I get a menu allowing me to choose between at least booting WinXP (sda3) and Linux (sda7)?
 
I am not worried about the RAID aspects right now (or should I?)
 
I did an fdisk -l, results below.
 
sudo fdisk -l
 
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016
 
Device Boot Start End Blocks Id System
/dev/sda1 1 7 56196 de Dell Utility
/dev/sda2 8 13985 112278285 f W95 Ext'd (LBA)
/dev/sda3 * 13986 18845 39037950 7 HPFS/NTFS
/dev/sda4 18846 19451 4867695 db CP/M / CTOS / ...
/dev/sda5 8 12500 100349991 7 HPFS/NTFS
/dev/sda6 12501 12769 2160711 82 Linux swap / Solaris
/dev/sda7 12770 13985 9767488+ 83 Linux
 
Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016
 
Device Boot Start End Blocks Id System
/dev/sdb1 1 7 56196 de Dell Utility
/dev/sdb2 8 13985 112278285 f W95 Ext'd (LBA)
/dev/sdb3 * 13986 18845 39037950 7 HPFS/NTFS
/dev/sdb4 18846 19451 4867695 db CP/M / CTOS / ...
/dev/sdb5 8 12500 100349991 7 HPFS/NTFS
/dev/sdb6 12501 13985 11928231 e W95 FAT16 (LBA)
 
Kind regards & tips much appreciated ...

---

### Post by Jon_J on 2009-10-08
Get Super Grub iso. [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
Burn it to a CD and use it to boot, or use unetbootin to install the iso onto a usb stick, and boot with usb.
I used the "automatic grub fix" (I think that is what it's called)
My situation is different than yours, since I deleted the Dell partitions.
I have a mini-10 (1010)
I have win-xp on sda1 and xubuntu on sda6
sda2 is data (ntfs), sda3 is extended, I have no sda4, sda5 is linux swap, sda7 is empty at the moment.
Anyway, I tried to install lubuntu (ubuntu 9.10 with LDXE desktop) to my sda7 partition.
The installer failed, and it must have failed while it was updating Grub.
Upon next boot, I got "Grub error 15" (file not found)
This means Grub cannot find menu.lst
In my situation, I think the failed installation moved or destroyed the Grub entry in the MBR (master boot record).
One other thing I may mention. Windows prefers to be installed onto the first partition.
Usually when installing an "experimental" OS/distro, I choose NOT to let the installer update Grub.
It writes to it's own /boot/grub/menu.lst file and I later copy/paste these new entries 
to my "working" menu.lst, which is in sda6 in my xubuntu installation.

---

### Post by jlbakker on 2009-10-24
Thanks for your response. SuperGrub didn't change anything.
Meanwhile I started a new thread with new information.

---

