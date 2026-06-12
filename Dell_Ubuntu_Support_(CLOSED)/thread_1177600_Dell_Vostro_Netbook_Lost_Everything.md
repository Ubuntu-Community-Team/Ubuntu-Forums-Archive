---
title: "Dell Vostro Netbook Lost Everything"
date: 2009-06-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jedlikewhoa on 2009-06-03
Hey everyone, fairly new to the linux operating system and it will be apparent by my problem.  I was deleting some old stuff (after installing and update, etc.) and now my computer boots up to a black screen where a terminal pops up.  
I decided it would just be easy to get my boot disk that dell gave me and just reboot ubuntu 8.0.4. In order to do this, though, i have to have an external cdrom drive (which i have).  It was never hooked up when the computer could boot up so i am not sure if the usb is even recognized.
Please help me!

---

### Post by anjilslaire on 2009-06-03
If you just want to reload the OS, plug in your cd-rom, insert the disc, power up, press "0" at the Dell logo, select the cdrom to boot from, and then follow the prompts to reinstall (which will likely erase all of your data).

---

### Post by jdacronym on 2009-06-03
Forgive me if I missed something, but couldn't jedlikewhoa recover his/her files by mounting his hard drive and copying or backing up things to an external drive, via a live session off the Ubuntu disk?  I did this once with a Windows XP user whose laptop had bitten the big one (she had zero trouble with the interface too, which is proof enough of ubuntu's friendliness to me).  

If [s]he has a Knoppix disk lying around too, there's probably scads of backup apps on it.  But that's another issue.

---

### Post by coffeeaddict22 on 2009-06-03
A third option is use the CD-ROM on a second PC to create a USB startup disc; you can then boot that up, backup all your important files (the whole /home directory if you've got room) and then reinstall.

---

### Post by anjilslaire on 2009-06-03
Yes, these are certainly viable options. The OP was having trouble even just connecting the usb cd-rom, so I gave simple instructions.

---

### Post by jedlikewhoa on 2009-06-04
Haha alright silly operator error on my part.  So i burnt the 8.0.4 ISO image to a CD and ran that on my external cdrom. Works great and is able to be read, but as soon as I get to page 4 of 7 it asks me how i want to partition my hard drive. Unfortunately i am unable to get past this screen and is asking for a root.  Is there anyway around this? thanks.

---

### Post by coffeeaddict22 on 2009-06-04
You will need to make some decisions on the partition screen.
I´m guessing the partitioner can still see your previous install, which will be causing a little angst.  Take the manual install option, select the existing partition in the page that comes up, and delete it.

You need 2 partitions: one for the OS, and one for swap.  Most punters (after their first reinstall :-( ) go for three: the screen you get to if you select manual partition asks you how big each partition should be, the mount point (which directory goes in it), and the filesystem type.

You need one for / also known as root; that´s where the OS goes.  A really big install with tons of options won go over about 15 GB, and it&#347; usually half that.  If you´re going to collect source files, maybe 20 GB at a rough guess..
The second one you don´t really have an option on is the swap partition; Linux uses a partition where other OS use a file.  It´s tidier, and it should be the same size as your RAM.
There´s a strong recommendation for a third partition: the mount point should be /home .  This essentially means that if(when) you reinstall, you can delete the files in the old OS without losing your personal files.  If you don´t do this, your personal files will be in the / partition, so it should be bigger again.

The filesystem is your last choice.  There´s a ton of options; it depends on your need to have data security on the drive.  ext4 is the new kid on the block, and is said to be faster; ext3 is the default, and works fine for all practical purposes.  Swap has it´s own file type.

---

### Post by jedlikewhoa on 2009-06-06
So if i do perform this as you suggest would i always have something plugged into the usb? There was hardly anything on the system before i deleted it all, i just didnt want to have to buy a dvdrom in order to load the disk that came with the computer. I figured there was a way to reclaim all original settings. Thanks again.

---

### Post by coffeeaddict22 on 2009-06-06
No, the install process transfers the files onto your hard drive, and the USB is only needed to get the files from the disc to the machine.  Same as any operating system/ program; you get it from somewhere (usually as a CD/DVD) and install it.  That's all you're doing.  It's a fair bet that the system will be the way it was when you bought it once you've reinstalled.

---

### Post by jedlikewhoa on 2009-06-08
Thanks a bunch. I've got it up and loaded and running now. I'm not sure if it has anything else wrong with it because the sound does not seem to be working. Or i could just be overlooking something very basic, but i did put both the player and netbook master control to the max. Any help would be great. Thanks.

---

### Post by sirebral on 2009-06-08
several hours late, but you booted up to a terminal you probably accidentally deleted the gnome window manager.  Too late, but maybe you can learn about that.

as for your sound, right click on the speaker in your panel and check the settings and levels.

---

### Post by jedlikewhoa on 2009-06-11
Yeah way too late. So i checked all the volume controls and it appears as though they are all up to max, yet i still can't get any sound to come out of the speakers. I've been reading about some terminal codes that have been "fixing" this problem for newer editions of ubuntu.  Is there anything else that might be the problem?

---

