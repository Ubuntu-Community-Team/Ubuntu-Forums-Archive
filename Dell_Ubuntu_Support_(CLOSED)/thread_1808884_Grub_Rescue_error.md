---
title: "Grub Rescue error"
date: 2011-07-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by NevynDragi on 2011-07-20
I've got a bit of an issue. It appears i managed to delete all of my partitions and the only thing i can get to pop up on my screen is a grub error :no such partition. As far as i know i have no operating systems or partitions on the laptop harddrive at all.

I tried to install windows with different bootable cd's but they wont boot because the grub loader pops up first. I have the boot order set to CD rom first. I even tried setting it up so it would only load from the cdrom but i just got an error that no bootable devices were found.

So i tried a bootable flash drive with backtrack on it. But i get an initramfs/busybox error so i can't load backtrack either. 

I'm kinda at a loss on what to do. Any suggestions?

The laptop is a dell inspiron 1525

---

### Post by oldfred on 2011-07-21
Welcome to the forums.

If you deleted the partition with the rest of grub then you get the boot error. But if you are getting it when you boot other devices, they are not booting.

Your CD drive could be broken (or lens needs cleaning) or the CD is not a bootable CD. Do you have a known working bootable CD that you can test with.  Can your system boot USB drives? Again the flash drive has to be bootable and the BIOS set to boot the USB device or on my system it is one of the "hard drive" choices.

Is your windows CD a full install or just an update version. Updates will not work unless you already have a system installed?

---

### Post by NevynDragi on 2011-07-23
They are working bootable CDs and the dvd drive on the laptop works just fine. I've checked the cds in other computers to double check. The drive worked fine before the crash, but i have no way of checking it now. I'm going to assume that the drive is still good since it booted one of the said bootable cds before i deleted the partition. I can boot from USB and i do have bootable Backtrack installation on a drive...but the Backtrack version seems to have issues with the laptop. It takes me to a boot menu and then crashes out. The only thing i can think of is trying to get another bootable small linux distro on another usb then using that to format and start over, but i was hoping to avoid that if possible, maybe just by using some grub commands or somethin. I just don't know anything about grub and all of the info i read so far hasn't helped.

---

### Post by oldfred on 2011-07-23
If you deleted the partition there is no grub to boot. The bit of code in the MBR just jumps to the partition to continue to boot.

Windows also puts just a bit of code in the MBR to jump to the windows PBR to continue to boot and the PBR knows to boot XP or Vista/7 depending on which you have installed.

Your issue with the CD is between BIOS and your CD drive/CD. If it is not booting CD or not trying to boot CD first then it jumps to the MBR of the hard drive.

I think a few systems seemed to require you to both set BIOS to boot CD and also use one time boot key and choose CD to get it to work.

You can restore a windows boot loader from Ubuntu's liveCD or any of many repair CDs that are available.

---

### Post by NevynDragi on 2011-07-23
I set the bios to boot from CD as number 1. It just doesn't even attempt it, its weird. It runs thru POST and then bam GRUB is up. Doesn't even give me the option to press a button to boot from cd. The whole load takes like 10 seconds. So i can't do a LiveCD or a Windows disc even, because it never even attempts to load it. Hell i even set it so my bios only recognizes my CD drive and it just jumped to a screen saying i was screwed because it didn't recognize squat.

---

