---
title: "Boot Problems (noob problem?)"
date: 2005-12-25
forum: Desktop Environments
---

### Post by mikimis on 2005-12-25
Okay, here's the setup...I have a Dell laptop with an 80 gig hd and WinXP.  I got a Seagate 300 gig exthd for xmas and am connecting it to the laptop via USB.  

I installed 5.1 on it, with appropriate partitioning (done with the install partitioner)  I got through the entire installation alright, up until the part where it tells you to reboot to make sure GRUB can load Ubuntu and any other OSes.

Now, GRUB loads up fine and lets me select XP or Ubuntu.  XP boots fine.  Ubuntu starts to boot but then displays the following:

> Booting command-list
root(hd1,0)
 Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/sdb1 ro quiet splash
  [Linux-bzImage, setup=0x1c00, size=0x124b15]
initrd /boot/initrd.img-2.6.12-9-386
  [Linux-initrd@0x1f30e000,0x4b57dc bytes]
savedefault
boot
Uncompressing Linux...Ok, booting the kernel.
Loading, please wait...
ALERT! /dev/sdb1 does not exist.  Dropping to a shell!
[4294680.803000] sdb:assuming drive cache: write through
[4294680.804000] sdb:assuming drive cache: write through


What do I need to do/change for everything to boot normally?

---

### Post by kaamos on 2005-12-25
It seems like installing to an external usb drive requires a bit more steps. Look here: [http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)

Hope you get it to work!

---

### Post by pharcyde on 2005-12-25
It looks like grub doesn't know where to find your ubuntu partion.

> 
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/sdb1 ro quiet splash


Are you sure "/dev/sdb1" is the location of ur ubuntu install?

---

