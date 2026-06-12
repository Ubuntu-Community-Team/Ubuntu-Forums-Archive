---
title: "Grub boot problem"
date: 2006-06-02
forum: Desktop Environments
---

### Post by Mike Easter on 2006-06-02
Short version: 2 hdd - hda ie #1 is Win98se - hdb ie #2 is new install of Ubuntu 6 from liveCD boot safe mode.  Problem: grub was installed on both hda & hdb but hdb won't boot.

Longer version:  mobo MSI K7T266 Pro2-A with 2 hdd, #1 or hda is an 80G Seagate with 4 fat32 partitions parted with an old PowerQuest PartitionMagic4 --  #2 or hdb is a 5G Quantum/Maxtor with 2 parts linux ext2 mostly and 256meg linux swap created by ubuntu install,  which is where I installed ubuntu 6.06 after booting with the live CD desktop.

My BIOS will let me boot from whichever drive or CD I want, and I would have preferred to control my own boot management with GAG on a floppy or hdd -- but instead what ubuntu did was put grub on the hda #1 and hdb #2 and the install on the hdb #2.  Now the problem is that I can't boot into ubuntu from the hdb #2 with gag or grub, getting an error.

After the install, my normal boot to hda or Seagate  became grub with ubuntu and win choices which would only boot into Win.  Since then I've replaced that hda grub with GAG.  Neither will boot into the hdb.  Same error for grub was on hda as described below when I try to boot hdb.

When I try to boot hdb, grub again gives me ubuntu and win choices, but in this hdb one none of which work.  The screen after failure to boot ubuntu says 
ubuntu, normal 2.6.15-23-386
root (hd1,0) 
file system is fat, partition type 0xc
kernel /boot/vmlinux-2.6.15-23-386
root=/dev/hdb1 ro quietsplash Error 15
File not found

<there might be some errors there, I jotted notes, not copied>

What I would like to do would be to try to repair the problem with the boot sector of hdb, preferably with something like a linux floppy boot so that I don't have to work with hammer and chisel typing things.  I really hate typing long commands, but I can do a little without making too many mistakes.

The other thing I was thinking was that if I gave grub the right commandline I could boot into hdb and somehow command a boot sector, like fdisk /mbr for Win9x.

I realize that I could reinstall, but I'm somehow figuring it is going to do the same thing.  I had a similar grub problem with Mepis once, but somehow I worked it out with GAG.  But I can't seem to do that this time.

Thanks in advance for any help;  and sorry about my aversion to commandlines.  I'm a fair typist except when I'm commanded, and then I just go to pieces ;-)

Mike Easter

---

### Post by Mike Easter on 2006-06-03
Pardon my ignorance and confusion about mbr and root partition.  

In searching for solving my problem I found this thread [http://www.ubuntuforums.org/showthread.php?t=24113](http://www.ubuntuforums.org/showthread.php?t=24113) 
HOWTO: Restore GRUB (if your MBR is messed up)

but I'm such a stranger to these commandlines and navigating that I need a little handholding to help me apply what is in there to my own problem.

Or perhaps I should make a boot floppy like here [https://wiki.ubuntu.com/GrubHowto/BootFloppy](https://wiki.ubuntu.com/GrubHowto/BootFloppy) This how to describes making a GRUB boot floppy

and then use that boot floppy to try to fix things.

I'm trying to fix hdb so that I can boot from it.

Mike Easter

---

### Post by Mike Easter on 2006-06-03
[QUOTE=Mike Easter]

When I try to boot hdb, grub again gives me ubuntu and win choices, but in this hdb one none of which work.  The screen after failure to boot ubuntu says 
ubuntu, normal 2.6.15-23-386
root (hd1,0) 
file system is fat, partition type 0xc
kernel /boot/vmlinux-2.6.15-23-386
root=/dev/hdb1 ro quietsplash Error 15
File not found
[/QUOTE]

I found the problem.  For some reason when my system boots from the 2nd drive, that causes grub to think that the 2nd drive is the first drive.  So, in order to boot, I have to get into grub commandline editing mode and change root (hd1,0) to root (hd0,0) and then I get the hdd boot.

My new problem is that I can't edit the grub menu.lst to make that change permanent, because the permissions are for root not me and I don't know how to do things as root yet.  But I'm learning.

Mike Easter

---

### Post by Mike Easter on 2006-06-03
[QUOTE=Mike Easter]My new problem is that I can't edit the grub menu.lst to make that change permanent, because the permissions are for root not me and I don't know how to do things as root yet.  But I'm learning.
[/QUOTE]
Got it.  sudo gedit and then navigate to the menu.lst and make the changes and save.

When I just navigated there and opened the file it wouldn't let me save it because it had root permission.

Now I made another discovery.  It boots properly that way when I change the boot order in the BIOS function, but when I use the GAG bootloader for linux which is on the #1 hdd, it doesn't work -- because then I guess the root (hd0,0) is wrong;  ie the linux boot is now the 2nd hdd recognized, no longer the first.

A fine pickle.  I guess I'll do it with the BIOS and not with GAG.

Mike Easter

---

