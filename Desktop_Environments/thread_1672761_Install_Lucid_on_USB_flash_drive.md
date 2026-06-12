---
title: "Install Lucid on USB flash drive"
date: 2011-01-21
forum: Desktop Environments
---

### Post by treacl on 2011-01-21
I'm about to order a USB flash drive to install Lucid on. Question is, do I need 16gb or will 8gb do for my purposes?

After install, I'll strip it down as much as possible: it will have Gnome and a web browser, but probably not OpenOffice, printing, any of the graphics programs, etc. Also, it won't mount the system's hard drive, so home, swap, etc. will all be on the flash drive. (I have minimal home requirements.)

Second question: To minimize use of swap, I'd like to maximize use of RAM. Is there any problem with installing 64-bit on a flash drive?

Many thanks,
treacl

---

### Post by oldfred on 2011-01-21
Flash drive is just like another hard drive, but slower since writes to flash are slow and USB port is slower than SATA. So 64bit is not related to flash but if computer supports 64 bit. Most new computers support 64 bit and most older computer that were just 32 bit will not boot USB flash drives anyway. 

You can use 8GB, a few have squeezed into 4GB but barely have room for anything and have to constantly houseclean. But flash drives have dropped a lot in price. I used a no name Microcenter flash drive about a year ago and now the same drive is down to about $1.50 per GB.

Be sure to use manual install so you can choose to install grub to the flash drive's MBR or else it will default to you internal drive.

It does not have to be encrypted:
Standard full install to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sdb1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You normally want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.

---

### Post by treacl on 2011-01-21
Thanks, oldfred; that's helpful. I've been using noatime and zero swappiness on my laptop for a while now, but the points about installing grub on the flash drive and using the noop I/O scheduler are well taken. --treacl

---

