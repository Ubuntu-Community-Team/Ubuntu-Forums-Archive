---
title: "[SOLVED] Can't dual boot Windows"
date: 2008-07-12
forum: Desktop Environments
---

### Post by morty35 on 2008-07-12
I set up a partition of 25 GiB of free space to use for a Windows XP dual boot (already have Ubuntu installed).  When I try to load up windows using an XP install disk, it says:

Setup did not find any dard disk drives installed in your computer?

How do I get my computer to install XP on the free partition?

---

### Post by eismcsquare on 2008-07-12
As far I know, for dual boot, you hvae to install Windows first, and then Ubuntu. So much for playing 'nice' from Microsoft.

But do let me know if I am wrong.

---

### Post by rsambuca on 2008-07-12
Make sure that the empty partition is formatted as ntfs.  Then Windows should be able to see it.

---

### Post by morty35 on 2008-07-12
I tried that and it still doesn't work.  I can't figure out what's wrong.  The partition is the first partition in the drive (which took forever to do).  It is 25 GiB and I tried formatting it as FAT32 and then NTFS.  I can't see why the windows CD can't recognize the partition.  What could be going wrong?

---

### Post by rsambuca on 2008-07-12
Sorry, I am out of any useful ideas here.

---

### Post by sandysandy on 2008-07-12
post output of

sudo fdisk -lu

---

### Post by Shippou on 2008-07-13
I have encountered the same problem as yours, though not exactly. My known solution is you backup all your files, reformat the hard drive (**all** of its partitions, setting up others on the way) then reinstall Ubuntu.

That problem took at least 5 reformats for me, in the course of 2 days. Done it this week. :)

---

### Post by logos34 on 2008-07-13
Is the target partition a primary of logical?  You can't put windows on a logical (unless there's a preexisting windows installation).  You'll get a similar error message

Edit: now that you;ve posted fdisk I see that the partition is sda3, primary, so that can't be it

---

### Post by morty35 on 2008-07-13
I ran the code sudo fdisk with the following output:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0006d0f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *    51263415   224829674    86783130   83  Linux
/dev/sda2       224829675   234436544     4803435    5  Extended
/dev/sda3              63    51263414    25631676    b  W95 FAT32
/dev/sda5       224829738   234436544     4803403+  82  Linux swap / Solaris

Partition table entries are not in disk order

It is now presently in FAT32 format.  By the way, I have realized that this post doesn't belong in this category, so I have reposted it in another thread.  Here is the link: [http://ubuntuforums.org/showthread.php?t=857855](http://ubuntuforums.org/showthread.php?t=857855)

I have searched online under windows forums and found what may be the problem.  I think because my machine Hard disk drivers are not on my Windows XP cd.  This is a Dell Inspiron 1420.  I don't know how to install the drivers so that windows recognizes the hardware because this computer doesn't have a floppy drive.  I am not sure what to do.

---

### Post by morty35 on 2008-07-13
What is a primary of logical?  How do I check if it is?

Edit:
nevermind, I just saw your updated post.

---

### Post by Pentie on 2008-07-13
you've got to make the first partion FAT or FAT32 so that XP could be loaded, as in my computer, i make a FAT /boot at the begining of my harddisk, and a logical partion at the last about 5G formatted as NTFS, and now both ubuntu and xp works well~

i install xp after ubuntu, but after that i've to boot with LiveCD to have grub installed in mbr~

---

### Post by ramaswamyps on 2008-07-13
windows can be installed in primary partition only.
if your ubuntu is in c: position move it to another partition and then you can install windows.

---

### Post by Wraith021969 on 2008-07-13
Is is a XP2 version? If you have an SATA drive the older versions of the cd dont recognize the interface and give a drive not found issue. I had a older version and had it installed and updated to sp2, so when i needed to fix my MBR with the win cd it wouldnt let me cause it was apparently the wrong version on the cd suddenly. I then found a step by step on slipstreaming sp2 into a new cd with power iso and the new cd i made recognized the sata interface. Bottom line find a torrent with win Xp sp2 :P. Ya Ya I rambled.

---

### Post by morty35 on 2008-07-13
I fixed it but now I have a different problem.  The problem was that my Windows XP disk did not have a driver for a SATA HDD.  I found a web page that explained the process:
[http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml](http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml)

I installed Windows XP, but and then I couldn't see Ubuntu.  I expected that, because the forum posts I looked at said that would happen.  Well, I think I ruined my GRUB bootloader.  It said ERROR 15, File Not Found.  I looked for /GRUB/boot/stage1 and it was not there, when it was there before.  So I basically ruined GRUB.  I then tried reinstalling Windows taking up the entire partition, and then installing Linux from scratch.  

After installing Ubuntu, I restarted the computer and got:  

Error Loading Operating System

I have no clue what to do at this point.  I can load Ubuntu using the Live CD, but that is about it.  I really don't want to have to reinstall Windows, because I took forever installing updates and drivers and getting the settings the way I wanted them to be.  Sorry for the long post.

---

### Post by morty35 on 2008-07-14
I figured out a way to do it. I decided to not partition it until during installation. So I deleted the Ubuntu partition, made it one long NTFS, and loaded Ubuntu. The grub was reinstalled and now I have a dual booted system. This has been quite the hassle.

SOLVED

---

