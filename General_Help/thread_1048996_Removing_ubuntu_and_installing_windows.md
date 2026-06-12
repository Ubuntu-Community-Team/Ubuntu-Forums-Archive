---
title: "Removing ubuntu and installing windows"
date: 2009-01-24
forum: General Help
---

### Post by ybh305 on 2009-01-24
Hi, I've been trying to remove linux and install windows for the past 4 days now and every time I try to install Windows, I get an error saying something like:

"Windows encountered an error and will stop to prevent damage to your computer"...etc..etc.

I was told to partition my HD and so I did. I have attached a picture to show you what gparted looks like.

I think the problem is that although I partition my HD the directoy /dev/sda still exists, which as you know, its for linux. And I think thats where Windows goes into conflict. I've tried changing the partition to FAT32 and NTFS but no luck.

I've also tried to run my Windows 98 CD and create a partition through the fdisk command and after doing that trying to reinstall but no luck.

In addition, I have downloaded KillDisk to wipe everything off and again, no luck.


I'm currently running on LiveCD of ubuntu on my laptop.

---

### Post by AndrewRoman on 2009-01-24
Which version of windows is it? And have you previously had windows on this HD?

---

### Post by powermonkey on 2009-01-24
I am confused.

/dev/sda is the path to your physical hard drive, it will always show up in your LiveCD.  Much like /dev/mouse points to the mouse on your laptop, etc.  No worries there.

Also can you explain when the BSoD pops up (the blue screen with the error)?  Does it occur as soon as the Windows install disk boots, or is it at a later stage, lastly which version of windows are you trying to install?

Possible problem is that you do not have all of the drivers loaded in order to install windows on your laptop.  Might have to write the drivers to a thumbdrive (if its Vista, or 7) or to a floppy and hit F6 (NT4, 2000, or XP) when it asks on the bottom.  I had this problem with my old laptop, the PATA chipset wasn't recognized by XP, causing a BSOD after the initial installation (the DOS looking one).  Another possibility is to use an SP2/3 installation disk.  As these will have most of the drivers loaded in.

---

### Post by SunnyRabbiera on 2009-01-24
keep ubuntu, really if you need help just ask...
Ubuntu can do the same things windows does except gaming, and wireless is iffy too but it can work for you.

---

### Post by step21 on 2009-01-24
First, I suspect you might be a troll, but anyway:

/dev/sda is not a directory but a representation of you main hard disk in the file system.

If you boot the windows xp/vista etc. setup cd, and then on the screen where it wants to know where you want to install it, just decide to format the whole disk, there is no linux at all left on your system. Any errors then are in no way related to linux.
And if you're really trying to install windows 98 ... not a good idea. Put that cd into the thrash quickly, your computer will thank you.

---

