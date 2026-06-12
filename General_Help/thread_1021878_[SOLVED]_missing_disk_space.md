---
title: "[SOLVED] missing disk space"
date: 2008-12-26
forum: General Help
---

### Post by Lucky-7 on 2008-12-26
I recently installed ubuntu 8.10 and must say that I am VERY pleased with the entire package.
I used the 8.04 installer and ran it through windows, I still have XP on the same HDD partition.

I have noticed recently (while trying to copy a file) that the available HDD space is incorrect, and by that, I mean that I have 12 gigs out of 108 available.  However, the disk usage analyser claims that I have 220 gigs (with 165 gigs available) 

While I dont need all that much space, 12 gigs is a bit frugal even for me, so I browsed this forum looking for clues.

I ran sudo fdisk -l and got this:
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

 Device Boot..........Start..........End............Blocks.............Id.......System
/dev/sda1...............1.................11..............88326.............de......Dell Utility
/dev/sda2...............12..............14164.......113683972+...7.......HPFS/NTFS
/dev/sda3...............14165.......14593.......3445942+.......db.....CP/M / CTOS / ...

running anything else has been inconclusive.

any advice?

---

### Post by Herman on 2008-12-26
:) It sounds like your file system isn't as big as your partition, (for some reason).
Sometimes that happens after restoring it from a backup. It's unusual to have that problem in a new installation, but the symptoms sound like that's the problem.

You can easily fix that by running GParted, which is in your Ubuntu Live CD.
Boot your Ubuntu live CD and open GParted. 
Just go 'System'-->'Administration'-->'Partition Editor', (GParted), you will be asked to type your password, and when GParted opens, it will show you a graphical view of your partitions.

Find your Ubuntu partition and right-click on it.
Probably you will then be able to click 'check', but if the option is 'greyed out', just click 'unmount first'. (Never, ever attempt to run a file system check on a partition while it's mounted).
After you click 'check', click 'apply' on the toolbar, then 'apply again in the confirmation window. 
A new window will open with a sliding bar moving crosswise backwards and forwards for a little while. 
GParted will run a file system check and then run resize your file system to fill the partition if it needs it, (it sounds like your does).
When that has finished, you can reboot and your problem should be solved.

Regards, Herman :)

---

### Post by ajcham on 2008-12-26
[thread=477198]This old thread[/thread] describes a glitch in the Disk Usage Analyzer whereby free space is overestimated. (for starters it would seem you only have a 120GB drive, not the 220GB as reported).

Since you installed in Windows (using Wubi, yes?) Ubuntu doesn't have it's own partition.  Instead it is using a virtual drive, the size of which you would have specified during installation.

First, try using Windows to establish how much free space is actually left on the drive, and if you have more than is being reported I believe it is possible to increase the amount of space available to Wubi/Ubuntu, either by increasing the size of the virtual drive, or by adding another one.  I don't know how you would go about this though, so you may need to do some searching, or perhaps someone else can fill you in on the relevant details.

---

### Post by Lucky-7 on 2008-12-26
Thanks you, I will try these.

anyone know of a way to increase the virtual drive space?

---

### Post by Lucky-7 on 2008-12-29
The issue was indeed WUBI

I resized it using LVPM and now have more than enough space.

still, I might upgrade to a full install later on, but for now, it`s 100% what I want it to be.

Thank you for your help!

---

