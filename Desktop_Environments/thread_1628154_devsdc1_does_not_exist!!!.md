---
title: "/dev/sdc1/ does not exist!!!"
date: 2010-11-22
forum: Desktop Environments
---

### Post by lapishc on 2010-11-22
After a recent update I can no longer boot into Ubuntu 9.10!

I get the following error (Have to type it, sorry I can't paste!)

Gave up waiting for root device
   -Boot args(cat /proc/cmdline)
       check root delay = did system wait long enough?)
       check root = (did system wait for right device?)

   -Missing modules ( cat /proc/modules; ls dev)
Alert! /dev/sdc1 does not exist dropping to a shell


This was completely out of the blue and my system has been working fine for > 1 year.  I am currently running a Dell T7400 Preceision

Thanks for your help in advance!!

---

### Post by SeijiSensei on 2010-11-22
How many drives does this computer have?  sdc usually refers to a second hard drive.

I don't know what kind of upgrade happened, but if the kernel was upgraded you'll see a menu of alternatives when the machine first boots.  The most recent entry at the top will boot by default. Instead, when you see the list, try scrolling down to the next oldest kernel.  It will probably be the third entry, as each kernel has a default and a "recovery mode" entry.  It should read something like this (though the kernel version will be different):

Ubuntu, with Linux 2.6.35-22-generic

See if that boots correctly.

---

### Post by lapishc on 2010-11-22
The machine only has one drive (sda1) and unfortunately I can not boot into any of the other entires.  Each time it hangs on "waiting for root file system"

Thanks for the reply, any other suggestions??!!

---

### Post by lapishc on 2010-11-22
I am fairly certain that somehow the machine has been confused and is attempting to boot sdc1 instead of sda1.  I am not sure how to re-direct the boot loader.  

The results of cat /proc/cmdline are...
BOOT_IMAGE=/boot/vmlinuz-2.6.31-22-generic root=/dev/sdc1 ro quiet splash

IF I only have one drive and it is on sda1 sdc1 should be sda1...right?

THANKS!!

---

### Post by SeijiSensei on 2010-11-22
You can edit the boot parameters on-the-fly using the techniques described [here](https://help.ubuntu.com/community/Grub2#Editing%20Menus%20During%20Boot).  

To make the change permanent, you need to edit (as root with sudo) /boot/grub/grub.cfg.  Note that this file is read-only for all users including root.  You'll need to do something like this:

```

cd /boot/grub
sudo chmod u+w grub.cfg
sudo nano grub.cfg
[make any changes you need from /dev/sdc to /dev/sda]; Ctrl-X + Yes to save
sudo chmod u-w grub.cfg

```

I know that grub.cfg tells you not to edit the file manually, but I have done so a number of times successfully.  Just be careful.  The only alternative is to [refresh the grub installation]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202") from a LiveCD.

---

### Post by lapishc on 2010-11-22
Hmmm, after changing the boot device (to sda1) at the boot loader menu I get the following new errors...

ata_id[376]: HDIO_GET_IDENTITY faield for /dev/.tmp/-block-8:16'
mount: mounting sys on root/sys failed: no such file or directory
mount: mounting dev on root/dev failed: no such file or directory
mount: mounting proc on root/proc failed: no such file or directory
Target file system doesn't have /sbin/init
No init found. Try passing init= bootarg

Any clue here?

---

### Post by SeijiSensei on 2010-11-22
It doesn't look like there's a bootable Linux version in /dev/sda1 either.

Something very wrong happened during whatever update you were performing.  Perhaps you had a USB drive attached which might have changed the drive identifiers?    

If you can boot from the LiveCD, try running "sudo fdisk -l /dev/sda" from a terminal then post the results here.  Maybe your Linux installation is in another partition besides the first?  Does the machine dual-boot Windows?  If so, then it's especially likely that the first partition is Windows and Ubuntu is installed in /dev/sda2 or above.

I'd give the "refresh the grub installation" approach I mentioned above a try.  It may straighten everything out for you without much heavy lifting on your part. Make sure you don't have any USB storage devices connected at the time so the only device will be the hard drive.

---

### Post by lapishc on 2010-11-22
Dear SeijiSensei,

Your premonition was right and your *nix skills are truly ninja-like. 

After refresh grub install and pointing the boot loader to the proper location all is well.  

Many thanks!!

---

