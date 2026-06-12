---
title: "Updates ?"
date: 2006-07-18
forum: Desktop Environments
---

### Post by jgcamp99 on 2006-07-18
When Ubuntu updates go to the core of Ubuntu, that is the kernel and gnome desktop update level, is the live cdrom download updated to that most recent version as well ? I guess, what I'm more interested in knowing, is that several hundred MB's of updates to the base OS and even the applications that come self-contained on the live cdrom (Open Office for instance) have occurred in the past 48 days. If ever, they are needed to be reinstalled or even installed on a new computer, it would probably be easier or just as time consuming (perhaps even less time consuming depending upon how far 6.06 is into it's LTS life cycle), to just get the latest iso and burn that to cdrom and start from there. I guess it'd be the equivalent of a Windows XP SP2 slipstream cdrom from the pre-SP2 retail cdrom ?

Reason I ask, earlier tonight, I gave Ubuntu 25 GB's more from Windows NTFS partitions. I booted XP and used Partition Magic to do this. The first few resizes of NTFS went smoothly, but the 4th operation bombed and the following subsequent operations cancelled. At that point I rebooted a couple times for Windows to figure out what was going on and then did the rest of the operations that bombed and cancelled thru Partition Magic again. It took it's time and ran it's course with no failures on the 2nd pass at it. But at the point of the first failed operation, I really wasn't too sure that Ubuntu was going to work properly once Windows XP was evicted of it's former NTFS space and the moving around of the other Linux partitions was done. I persisted thinking wth, the worst that can happen is that I have to reinstall Ubuntu. 

At any rate eventually all operations worked, Ubuntu works perfectly and I can see that there will be a day when Ubuntu Linux evicts Windows XP off this computer completely. The way I have it set up, the primary drive, Windows XP. The secondary drive, has NTFS data storage partitions and Ubuntu. I know it's cosmetic, but now that Grub is the boot loader of choice, I could basically delete and reformat the primary drive, even the NTFS storage partitions on the secondary drive and give it all to Ubuntu. To anyone else, I would still have Ubuntu that I've set up thus far and it would appear to be the only OS on the computer by just editing Grub to not even have Windows XP as a selectable OS choice. But in reality, I would know the primary OS (Ubuntu) is really on the secondary drive. When that day comes, Is there anyway to move Ubuntu to the primary hdd as it's been setup throughout the course of being on this computer without a major rework or mounting/mapping headaches ? Who knows, I may opt to start fresh/clean if Ubuntu updates it's iso images and do a clean install ?

---

### Post by orb9220 on 2006-07-19
Well I decide to keep a xp basic install with my wifi connection (6Gb). 
As really a precuation If Ubuntu or more likely myself breaks it.

Since I am still learning. Also I converted my large data partition to fat32 so that windowsxp could downloads something critical tha I could access with my ubuntu.

---

### Post by almahtar on 2006-07-19
> **orb9220 said:**
> Well I decide to keep a xp basic install with my wifi connection (6Gb). 
As really a precuation If Ubuntu or more likely myself breaks it.

Since I am still learning. Also I converted my large data partition to fat32 so that windowsxp could downloads something critical tha I could access with my ubuntu.

Having a FAT32 partition around is a great way to share information between Ubuntu and Windows, but what's worked even better for me was to have a EXT2 partition share that info.  There are a few GREAT EXT2 drivers available for Windows, and EXT2 makes better use of your hard drive space and has better speed than FAT32.

Either way is great though!

---

### Post by jgcamp99 on 2006-07-19
I have two 160 GB drives, Windows had all of it at 1 point in time. I keep XP, it's bought and paid for and is great for work related projects to have that kind of space. Ubuntu will eventually get the secondary drive, and will be what I mainly use for home and personal use. It's been 48 days since Windows was booted and perhaps I should keep it updated for the KB******'s that Microsoft issues.

As for sharing between Windows and Linux, I have a USB 2.0 external notebook drive and even a 1 GB memory stick that does that for Linux to Windows share, even when I want to share with OS X. For Windows to Linux share, the read feature for NTFS works fine, read from NTFS and copy to EXT3. With enough hdd space for both, they don't bump into each other. My Linux partition was originally set to 20 GB, now it's 35 GB including swap. I don't ever want a FAT32 partition, when a drive fails, the partition seems to corrupt. I had one do that and fortunately I had a recovery software program that was able to get back what I had on a FAT32 partition. That same drive that failed, stayed running good enough to get the ntfs stuff off it, but the partition itself was not corrupted like the FAT32 partition was. That was easy a simple backup process, but the FAT32 that recovery was a chore. I vowed never to use FAT32 ever again on the internal drives over that experience. The external drive is FAT32, but it's just a temporary landing zone and things don't stay on there very long, the drive doesn't remain hooked up very long, even when used.

---

