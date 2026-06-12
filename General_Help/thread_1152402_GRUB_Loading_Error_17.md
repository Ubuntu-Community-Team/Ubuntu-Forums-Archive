---
title: "GRUB Loading Error 17"
date: 2009-05-07
forum: General Help
---

### Post by mawil1013 on 2009-05-07
I installed xubuntu, then deleted all partitions/reformatted hard drive, eventually nothing left but a single partition. What I'm doing is taking xubuntu off the laptop and installing 98, I'm putting U9 on a desktop that I have. Anyway I forgot that ubuntu has to be uninstalled in a particular way and screwed up.

I have tried Super Grub but it doesn't help, 

I boot the laptop and get,

GRUB Loading stage1.5
then
GRUB loading, please wait...
Error17

Ii have read that it is a messed up mbr and SuperGrub cannot find it to fix it, It downloaded the ISO CD.

Now that I ran SUPERGRUB, When I boot I get 'Invalid system disk'.

I need big time help! I tried searching for an answer and basically all I saw was try SuperGrub.

UPDATE INFO: Booted xubuntu off cd, in terminal I enterd; sudo fdisk -l. This is what was displayed.

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a4fla4e

Device Boot
/dev/sdal *

Start
1

End
12161

Blocks
97683201

Id
c
System
W95 FAT32 (LBA)

---

### Post by caljohnsmith on 2009-05-07
If you don't have any OSes installed to the laptop, then of course you will get an "Invalid system disk" or similar error when you try to boot the HDD. You need to install some OS to the laptop if you don't want a boot error on start up.

John

---

### Post by mawil1013 on 2009-05-08
> **caljohnsmith said:**
> If you don't have any OSes installed to the laptop, then of course you will get an "Invalid system disk" or similar error when you try to boot the HDD. You need to install some OS to the laptop if you don't want a boot error on start up.

John

I've tried to reinstall xubuntu several times directly onto the hd, but because of the issue I cannot. I can run xubuntu off the disk. I tried loading 98 but error won't let me. I assume the easiest thing would be for me to get xubuntu reinstalled then do a proper uninstall? I just downloaded, Ultimate Boot CD from [http://ubcd.sourceforge.net/download.html](http://ubcd.sourceforge.net/download.html), and will try it this morning.

---

