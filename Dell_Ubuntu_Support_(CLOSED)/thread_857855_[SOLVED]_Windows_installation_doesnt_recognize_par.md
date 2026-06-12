---
title: "[SOLVED] Windows installation doesnt recognize partition"
date: 2008-07-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by morty35 on 2008-07-12
I am trying to dual boot Windows XP on a maching with Ubuntu already installed.  I have partitioned the drive with the first partition being a free partition.  I have tried to load windows from a CD but it says that Windows doesn't recognize any hard disk drives.  I have tried reformatting it to FAT32 and NTFS, but still the same problem.  How do I get windows to see the partition so that I can install windows XP.

---

### Post by PinkFloyd102489 on 2008-07-12
SATA drive?

---

### Post by morty35 on 2008-07-13
I don't know if it is a SATA.  From GParted, I got the device information to be a ATA Hitachi HTS54251.

I looked online at Windows forums and found their solution to be installing the Hard drive drivers on a floppy disk and installing them right before windows.  My problem is that I don't have a floppy disk drive.

---

### Post by morty35 on 2008-07-13
I have confirmed that it is a SATA HDD.

---

### Post by PinkFloyd102489 on 2008-07-13
You might need to load SATA drivers if you got a disc with the HD.

---

### Post by morty35 on 2008-07-13
I fixed it but now I have a different problem. The problem was that my Windows XP disk did not have a driver for a SATA HDD. I found a web page that explained the process:
[http://news.softpedia.com/news/Insta...F6-47807.shtml](http://news.softpedia.com/news/Insta...F6-47807.shtml)

I installed Windows XP, but and then I couldn't see Ubuntu. I expected that, because the forum posts I looked at said that would happen. Well, I think I ruined my GRUB bootloader. It said ERROR 15, File Not Found. I looked for /GRUB/boot/stage1 and it was not there, when it was there before. So I basically ruined GRUB. I then tried reinstalling Windows taking up the entire partition, and then installing Linux from scratch.

After installing Ubuntu, I restarted the computer and got:

Error Loading Operating System

I have no clue what to do at this point. I can load Ubuntu using the Live CD, but that is about it. I really don't want to have to reinstall Windows, because I took forever installing updates and drivers and getting the settings the way I wanted them to be. Sorry for the long post.

---

### Post by morty35 on 2008-07-14
I figured out a way to do it.  I decided to not partition it until during installation.  So I deleted the Ubuntu partition, made it one long NTFS, and loaded Ubuntu.  The grub was reinstalled and now I HAVE A dual booted system.  This has been quite the hassle.

SOLVED

---

