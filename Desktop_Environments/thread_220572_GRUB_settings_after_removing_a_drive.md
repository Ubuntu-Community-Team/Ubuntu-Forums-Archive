---
title: "GRUB settings after removing a drive"
date: 2006-07-21
forum: Desktop Environments
---

### Post by Nescientist on 2006-07-21
I need to RMA a hard disk, and I'd like to do it without breaking my GRUB setup. The disk in question has absolutely no boot information, installation info... it isn't even formatted, but because GRUB expects to find four SATA drives instead of the three that remain after I yoink the drive in question, it throws error 21 without even showing me a menu. Now, by my blind intuition I would think that simply editing the "device.map" and "menu.lst" files would have me all set, but since I don't have a boot cd with me at the moment I'd rather not do that without certainty ;).

Another concern is that since the error comes up before the menu does, I'm a little worried that the issue is not with GRUB's setup info pointing to a nonexistent drive but to the MBR pointing to the wrong drive to find GRUB. I haven't the beginning of a clue how to edit an MBR.

Here's my device.map file (sdb needs to go, sdd has my ubuntu install)
[INDENT](hd0)	/dev/hda
(hd1)	/dev/sda
(hd2)	/dev/sdb
(hd3)	/dev/sdc
(hd4)	/dev/sdd
[/INDENT]

and here's what I thought was the relevant portion of my menu.lst
[INDENT]
title		Ubuntu, kernel 2.6.15-26-amd64-generic
root		(hd4,1)
kernel		/boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sdd2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-amd64-generic (recovery mode)
root		(hd4,1)
kernel		/boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sdd2 ro single
initrd		/boot/initrd.img-2.6.15-26-amd64-generic
boot

title		Ubuntu, kernel 2.6.15-23-amd64-generic
root		(hd4,1)
kernel		/boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/sdd2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-amd64-generic (recovery mode)
root		(hd4,1)
kernel		/boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/sdd2 ro single
initrd		/boot/initrd.img-2.6.15-23-amd64-generic
boot

title		Ubuntu, memtest86+
root		(hd4,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
[/INDENT]

Is it possible for me to edit stuff in /boot/GRUB, shutdown, remove the device, and be able to boot up again immediately? Keep in mind that if I screw up, I'm without a computer for however long it takes me to get off my lazy butt and travel the five minutes'  grueling commute home to grab a boot disk - a devastating eventuality :wink: . I'd like to get it right the first time.

---

