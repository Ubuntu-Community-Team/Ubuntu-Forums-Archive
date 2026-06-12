---
title: "Wipe the harddrive clean."
date: 2008-12-25
forum: General Help
---

### Post by linux noooob on 2008-12-25
How do I wipe the harddrive clean? By clean I mean no partitions no nothing and definatly NO GRUB. Many people say I should do some fansy stuff with a windows recovery cd. Well the only windows recovery CD I have doesn't have a terminal program or anything like it! Not to mention I don't have a floppy drive. Is there any way to wipe the drive clean?

---

### Post by oilchangeguy on 2008-12-25
> **linux noooob said:**
> How do I wipe the harddrive clean? By clean I mean no partitions no nothing and definatly NO GRUB. Many people say I should do some fansy stuff with a windows recovery cd. Well the only windows recovery CD I have doesn't have a terminal program or anything like it! Not to mention I don't have a floppy drive. Is there any way to wipe the drive clean?

yep, just boot from your ubuntu cd. locate the partition manager, and simply delete all partitions.

---

### Post by Steve1961 on 2008-12-25
Boot with a live cd and make sure you know how linux names your drive, e.g. hda, sda, etc (use fdisk -l to find out).  Then, assuming the drive is hda, just do this:

sudo dd if=/dev/zero of=/dev/hda count=1 bs=512

This will wipe out the partition table and all  installation programmes will now see this as a raw drive

---

### Post by Howitzer777 on 2008-12-25
well you have an xp install disc right? or any win install disc you should be able to go on it and then you'll see an option to go into a terminal. otherwise you can do it on ubuntu. someone will prob tell you how to do that but i don't know any of those codes

---

### Post by linux noooob on 2008-12-25
double post ignore sorry

---

### Post by linux noooob on 2008-12-25
> **Howitzer777 said:**
> well you have an xp install disc right? or any win install disc you should be able to go on it and then you'll see an option to go into a terminal. otherwise you can do it on ubuntu. someone will prob tell you how to do that but i don't know any of those codes

There isn't one it is just put in and it automaticly does it!

---

### Post by oilchangeguy on 2008-12-25
> **Howitzer777 said:**
> well you have an xp install disc right? or any win install disc you should be able to go on it and then you'll see an option to go into a terminal. otherwise you can do it on ubuntu. someone will prob tell you how to do that but i don't know any of those codes

won't work if it's a factory restore cd. has to be a true windows cd. and the command in windows is diskpart. see this link: [http://support.microsoft.com/kb/300415](http://support.microsoft.com/kb/300415)

---

### Post by linux noooob on 2008-12-25
> **steve1961 said:**
> boot with a live cd and make sure you know how linux names your drive, e.g. Hda, sda, etc (use fdisk -l to find out).  Then, assuming the drive is hda, just do this:

Sudo dd if=/dev/zero of=/dev/hda count=1 bs=512

this will wipe out the partition table and all  installation programmes will now see this as a raw drive

thank you thank you thank you!!!!

---

### Post by linux noooob on 2008-12-25
It all worked fine but after I re-made the harddrive table into msdos and reinstalled windows from the recovery CD (which does work because I have done it on other computers) it doesn't load it just shows a blank screen. The CD recovers windows XP SP1 could the problem be because sp1 doesn't support SATA harddrives?

---

### Post by Steve1961 on 2008-12-25
> **linux noooob said:**
> It all worked fine but after I re-made the harddrive table into msdos and reinstalled windows from the recovery CD (which does work because I have done it on other computers) it doesn't load it just shows a blank screen. The CD recovers windows XP SP1 could the problem be because sp1 doesn't support SATA harddrives?


Well if you managed the installation with the cd, which if it's a recovery cd should have the drivers already on it, It sounds unlikely that it's to do with the SATA drive.  Does the PC boot at all?  Can you enter safe mode by hitting f8 when booting?

---

### Post by linux noooob on 2008-12-25
well to go into the BIOS I have to hit F8 but after the BIOS nothing loads I just get a blinking _

Also It did boot before I did this. Last question is what are the chances and risks of just copying my parents IDE hard drive to the sata harddrive using gparted on the live CD?

---

### Post by Steve1961 on 2008-12-25
> **linux noooob said:**
> well to go into the BIOS I have to hit F8 but after the BIOS nothing loads I just get a blinking _

Also It did boot before I did this. Last question is what are the chances and risks of just copying my parents IDE hard drive to the sata harddrive using gparted on the live CD?

Ok, first check that xp has installed.  You can do this again with a live cd to have a look at the xp partition to make sure it's populated.  If it is it sounds like the mbr hasn't been installed properly.  Generally you can do this by using the recovery console on an xp installation disk and typing fixmbr at the prompt.  However, I don't know if you have this option on a recovery cd.

As for copying your parents ide drive contents, it's unlikley to work properly because of hardware differences.  If you can't get hold of a disk to fix the mbr try reinstalling again

---

### Post by linux noooob on 2008-12-25
FOUND THE PROBLEM!!! Didn't set the partition flag to 'boot' in gparted!

---

### Post by Steve1961 on 2008-12-25
> **linux noooob said:**
> FOUND THE PROBLEM!!! Didn't set the partition flag to 'boot' in gparted!

Ahhh... that would do it :) although the xp installation should really have taken care of that.  Oh well, all sorted.

---

