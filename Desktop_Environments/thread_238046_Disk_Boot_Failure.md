---
title: "Disk Boot Failure"
date: 2006-08-17
forum: Desktop Environments
---

### Post by Xilon on 2006-08-17
I installed Ubuntu on my new SataII HDD a couple days ago, and everything worked fine. While paritionning the drive I left a 20gb FAT32 partition empty in case I wanted to install Windows on it. The time came (unfortunately I need Windows to develope programs for it for my Uni course... which is odd), I tried installing windows XP on the FAT32 partition but when I got to the screen where it asks which partition to install to it said that it can't find a Windows XP Compatible partition (I can't believe Windows is stupid enough not to recognise it's own partitions...), so it was a no go. I restarted the computer and wanted to boot into ubuntu...
"DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER." :-x 

I think I know who the culprit is... but how do I fix this and get my ubuntu back? :( Also is there any chance of actually installing Windows?

---

### Post by mcman42 on 2006-08-17
Well you probably can not boot because windows some how edited you Master Boot Recorc or whatever that is called. You have to boot from LiveCD and tr editing it manually.

It was a long time since I nstalled windows. Does it have on opyion to format a drive to get a proper partition for install? If it does then jst choose those 20gb of fat32. 

I will try to help further if you will come up with more specific questuions.

GL

---

### Post by Xilon on 2006-08-17
I did try that, which is probably why it messed with the MBR. When I delete the partition and try to create a new one (as I tend to do) it just creates a "raw" partition and says that there are no compatible partitions... yet there are 3 fat32 partitions (only one is empty though)

What I want to do is either fix Ubuntu, or install windows and fix ubuntu.

---

