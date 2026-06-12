---
title: "Can't fix GRUB!"
date: 2005-06-21
forum: Desktop Environments
---

### Post by bigblop on 2005-06-21
I have Ubuntu installed on a HDD and have just installed WinXP on another HDD. But when I boot the computer I can only choose to enter WinXP. The old GRUB boot loader has been overwrittin.


I have downloaded the Ubuntu Live CD. I have then booted into this live CD and tried to open a console and write:

ubuntu@ubuntu:/$ sudo update-grub
sudo: update-grub: command not found
ubuntu@ubuntu:/$

But I get the above error. How do I fix GRUB so I can bot choose WinXP and Ubuntu Linux when I start the computer??

---

### Post by Nimefurahi on 2005-06-21
Is your XP system installed on your primary (or Master) HDD and your Ubuntu system installed on your secondary (or slave) HDD?

If that would be the case, I would transpose the two HDDs either physically or through BIOS if it allows such a "soft" transposition.
 
If after switching the two HDDs your Ubuntu boots up, you could include XP as an additional choice on your Grub menu and leave all else alone.
 
What have you got there, bigblop?

---

### Post by bigblop on 2005-06-21
I was told that I just needed to use the live CD and then change something in the grub menu. But for some reason it don't work. I don't want to switch the disks.

---

### Post by shof2k on 2005-06-21
We need to know which disk has ubuntu and which disk has windows.  Are they on separate disks, if so which is the primary and secondary.  If they are both on one disk but separate partitions, which partition is each OS on?

---

### Post by Dave_is_sexy on 2005-06-21
What's happened is that GRUB in the mbr has been overwritten. All it's config files will still reside in your /boot area.

And if you have already booteb ubuntu it must be on an area of the disk that can be read as boot (sometimes there are boundary problems)

So all you need to do is put grub back into your mbr. Dunno how to do that with ubuntu cos it's all very linear and automatic, but you can do it very easily with a Debian Woody installer disc. 

Probably a crap way but you can. think you can get images as small as 200mb from debian.org - but then i just use that cd for everything cos it's the only interactive piece of power i've used thus far.

---

### Post by duff on 2005-06-21
[QUOTE=bigblop]I have Ubuntu installed on a HDD and have just installed WinXP on another HDD. But when I boot the computer I can only choose to enter WinXP. The old GRUB boot loader has been overwrittin.


I have downloaded the Ubuntu Live CD. I have then booted into this live CD and tried to open a console and write:

ubuntu@ubuntu:/$ sudo update-grub
sudo: update-grub: command not found
ubuntu@ubuntu:/$

But I get the above error. How do I fix GRUB so I can bot choose WinXP and Ubuntu Linux when I start the computer??[/QUOTE]
If you have a network connection you can `sudo apt-get install grub`, then `grub-install`.  I've had to do this a while ago, but I think that's all there was to it.

---

### Post by Nimefurahi on 2005-06-21
I believe you to be correct in saying that your Grub boot loader was overwritten by the installation of XP. Perhaps Ubuntu (along with Grub) was installed on your first HDD. My guess is that you added another HDD and installed XP on it. This sounds reasonable in that you would have purposefully focused on another HDD, seemingly isolated from your Ubuntu system, believing that XP would play fair and not touch Ubuntu. Not so. XP doesn't play fair. If your system matches the above senario, XP has claimed the MBR of your first HDD for its own. That's right. Even installing the XP system on a secondary HDD it will hog-up what it can of the first HDD as well. Thank you Bill Gates!

My concern is that in trying to salvage Grub with a live CD on what may have been your first HDD, you may very likely destroy the XP boot loader (if it resides there) as well. Then, neither Ubuntu or XP will be accessable.

An experiential rule of thumb for multiple OS: Install the microsoft package first. Give it full berth and don't let it even see another OS. Then install the Linux with Grub on your first boot partition (not the MBR) and chainload the XP system from the Grub menu. 

So much for lessons... do you have a Grub diskette?

---

### Post by Dave_is_sexy on 2005-06-21
I wouldn't panic just yet. Grub boots Windows just fine. If windows isn't booting (it will) you can always add the bootflag to your windows partition as it still has it's own little boot.ini file

To add that bootflag you need cfdisk. Again I'd put my Debian Woody CD in and navigate down to "partition a hard disk" then just make sure the bootflag is on the xp partition and say "write to disk"

...but you shouldn't need to, and you need to be careful with that kinda stuff.

*glances back at original thread*

Is your Ubuntu install new aswell? If you just install it again it'll fix everything for you.

There are other solutions i know of but they're all a bit crap - but reliable. 

Your harddisks and data are fine. You're just missing a configured bootloader. 

From looking around the net (i'm bored of my own problems) it seems that installing grub by itself is a bit hard. The Debian site is terrible to navigate, but if you can find a business-card image, i'd go with that. otherwise get a full 600mb one - it'll be useful in the future anyway. (v3.0 not 3.1). Once you have it just navigate down to "install boot loader". That'll work right? People?

---

