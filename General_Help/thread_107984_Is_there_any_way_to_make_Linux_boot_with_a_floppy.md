---
title: "Is there any way to make Linux boot with a floppy?"
date: 2005-12-24
forum: General Help
---

### Post by XtremeGamer99 on 2005-12-24
I am about to install Ubuntu on my second hard drive. However, I want that to be bootable *only* if the floppy that has the boot stuff on it is inserted. Like, if it's not inserted, then proceed to boot into my primary linux, and if it is inserted, then give me the menu that lets me choose if I want to boot into the parimary hard drive or into the newly installed Ubuntu on my second hard drive.

I think I remember someone talking about this a while back. There was some option you could execute to install GRUB on a floppy when you install from the CD. I  just can't remember any of the instructions.

Thanks. =)

---

### Post by SickTwist on 2005-12-24
Sure, that is possible. Basically when you install Ubuntu on the second hard drive, you'll need to put grub on the floppy during the installation.

When the grub configuration asks you if you want to put grub on the MBR, select no/cancel/manual (can't remember the exact wording) then you'll get a screen asking you where to put it. Just type this in:

/dev/fd0

That is a zero after "fd", not the letter O. fd0 is the device file for your floppy drive. If it doesn't work let us know--I've never actually attempted this myself. All I know is that it is definitely possible to install grub to a floppy.

Also,  you'll need to make sure that your BIOS is set up to boot from floppy before the HDD. When there is not floppy in the drive, your BIOS will try to boot from the main HDD and it will find grub on the MBR from your other Ubuntu install :)

---

### Post by oxman on 2006-01-04
Hello,
I have three hard drives in my box.
hdb is FC4 (slave)
hdc is vfat32 (master)
hdd is 5.04 Ubuntu (slave)
The Grub loader is on /boot of my FC4 installation. I would like to keep it there.  I have installed a bootable grub file for ubuntu to the 1st partition of my ubuntu drive. I was going to simply copy the info from the ubuntu grub file on to the FC4 grub file. I am unable to access the unbuntu disk because the boot loader doesn't acknowledge yet. What exactly should I place in /boot/grub.conf of hdb (FC4 grub) so ubuntu is included as a boot option?
I tried going the route of booting ubuntu via floppy twice and it failed twice (the floppy is formated ext2). Don't know what the problem is there. It just fails. Is there an ubuntu emergency boot image for a floppy somewhere on line?
Thanks for any help. It is appreciated

---

