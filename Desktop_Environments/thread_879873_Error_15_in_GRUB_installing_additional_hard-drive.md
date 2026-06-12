---
title: "Error 15 in GRUB installing additional hard-drive"
date: 2008-08-04
forum: Desktop Environments
---

### Post by sodasound on 2008-08-04
Hi,

I guess this is the price for not doing things right the first time.
Here's the picture: I got things working sort-of good installing on an 80GB SATA Drive. I've got an old 80GB IDE which I've reformatted with Ext3 in gparted, which I couldn't read or write to. Then today I added a 160GB SATA Drive, which I intended for audio. Then I get Error 15 and I'm stuck. 

I've been at this for seven months, and while I know it's time to get to know how to bomb around in the shell, I'm a total n00b with it.

HELP!!!!!!

SS

---

### Post by sodasound on 2008-08-04
Hi, so I looked at the forums, and monkeyed around with hardware and SuperGRUB, and smoked a lot of cigarettes and drank a lot of coffee etc.

I came up with a nearly-100% success solution:

1. Get ALL of the hardware wired up so that BIOS recognizes it, and set a suitable boot order (ubuntu install disk location first).

2. Pop the disk in and choose "try Ubuntu without installing"

3. Poke around in the file browser and the Partition Editor to see what Gnome thinks is on Each drive.

4. Choose a drive to install on, then click the install icon.

5. at the point of formatting, choose manual formatting.

6. select each of the non-essential partitions on old drives that need to be freshened up, and delete them in turn (MUST KNOW WHICH ONES YOU WANT TO KEEP!)

7. Create a new Ext3 partition on drives intended to be storage drives and IMPORTANT, go back, and then install the system on the blank hard-drive you have chosen.

8. When asked if you want to import settings from your previous system, say YES!

When asked for my user-name and password, and the name of the computer, I superstitiously used the remembered values. 

When I rebooted, the Bootloader recognized several kernel's which either no longer existed or were broken. but the new vanilla kernel a few clicks down booted me into my old system, with all files and software intact. Now perhaps I screwed up, and I'll have to do this again, but it buy's me time to get things where I want them. I presume my files and software are spread over the two drives. And now there's a new SATA drive which I have reserved for audio/video. Now I just want to clean-up and organize: one drive for OS and documents, one for photos and music etc. and one for recording and editing. Any suggestions?

---

