---
title: "Very pissed off -- Ubuntu shredded four hours of thesis writing"
date: 2006-09-06
forum: Desktop Environments
---

### Post by MarinaraOfDeath on 2006-09-06
Dual booting windows and Dapper. Writing MS thesis in Kile. Some figures turn out to be mislabeled, so I have to boot into XP and spend a couple of minutes finding the array-indexing typo in a Matlab script and regenerating the figs. I go to copy the files to my thumb drive, and turns out that when I booted out of Dapper, it shredded a bunch of the files on that. Odd. So I check, and indeed my thesis files, located on a FAT32 partition, which I was nearly done with for the night and about ready to back up, are gone too, at least on the XP side.

Since I've been able to save data this way before, boot back into Dapper. But during boot I get a bunch of messages about how the OS is fixing files. I crack open the FAT32 partition in nautilus, and sure enough, a bunch of files of size 0 bytes, which wasn't surprising cause there were boot messages about recalculating file sizes since they contained incorrectly labeled free clusters. The partition where the files were located is FAT32 exactly so that I could share between operating systems. Basically, Ubuntu has seriously devolved over the last 4-6 weeks, lots of hard drive thrashing which didn't used to happen, no lockups but plenty of program crashes *which I didn't have before all the f'in updates*. At the same time Ubuntu is seeing my thumb drive as read-only, which has never ever happened before.

I don't know why it did this, but the OS should not recalculate file sizes ***without asking me***. That is a recipe for disaster since you (or at least I) cannot attempt to save the files. So, how do I modify that f!@#in behavior so that it asks instead of assuming I want my files "fixed"? It clearly is possible since I've gotten boot messages before about not automatically fixing detected changes in files.

---

### Post by peabody on 2006-09-06
Filesystems are mounted readonly when there are problems with them.  You have my condolences on your loss and waste of time.  However, it sounds like the filesystem may have been corrupted a while back and it finally decided to collapse on you.  It's hard to say whether this is dapper's fault (really, the kernel's vfat support fault) or if the same thing wouldn't have happened to you in Windows.

I was not aware that dosfsck runs at boot for any filesystem that isn't part of / (in other words, it's just some random filesystem under /media).  If this is the case though, I would also like to know how to disable this behavior as I'm under the impression that dosfsck is not that great compared to windows chkdsk (which isn't all that great either, I've had chkdsk destroy filesystems before).

---

### Post by whizbaby on 2006-09-06
Recalculating file sizes is usually done due to an already broken filesystem, so making backup copies is already impossible at that point. Not calculating sizes would mean to leave the drive inaccessible. When you use FAT32 be aware that it is an inferior easy-to-break filesystem (many occasions to break it).

---

### Post by MarinaraOfDeath on 2006-09-06
Thanks both of you. In fact the same thing occurred to me about two hours later. I may be able to get some of it back, there's a bunch of files named fsck00**.rec, which look like some sort of recovery files.

---

### Post by taurus on 2006-09-06
Not sure if you have done this but next time before you reboot your machine while in Ubuntu, unmount your thumbdrive first with the "umount" command before you remove it!!!  you are not supposed to just remove it like you would in Windows when the thing is still mounted...

---

### Post by WakkiTabakki on 2006-09-06
> **peabody said:**
> 
I was not aware that dosfsck runs at boot for any filesystem that isn't part of / (in other words, it's just some random filesystem under /media).  If this is the case though, I would also like to know how to disable this behavior as I'm under the impression that dosfsck is not that great compared to windows chkdsk (which isn't all that great either, I've had chkdsk destroy filesystems before).

Check your /etc/fstab
Each filesystem that is mounted has it's own line in here. The last field on each line (the 6:th one) is used by fschk to determine whether it is to be checked at boot time...
Just put down a 0 there, and fschk should leave it alone.

/N

---

### Post by MarinaraOfDeath on 2006-09-06
Oh, it was definitely supposed to have been unmounted already according to what nautilus (and a manual check of ls /mnt) returned.

---

### Post by whizbaby on 2006-09-06
You check what's mounted by the command **mount**(simply) and not by looking what's in /mnt. A drive could be mounted on /bratwurst/ketchup without problems and you wouldn't find it in /mnt. Besides in ubuntu automatically mounted drives are found in /media, not /mnt.

---

### Post by wpshooter on 2006-09-06
A simple way to keep this from happening, is to never put two different O/S on the same computer at the same time.

IMO, it is a disaster, just waiting to happen !!!

I have little enough confidence in one O/S working correctly, let alone two !!!

But hope you can come up with some way of getting your work back.

---

### Post by MarinaraOfDeath on 2006-09-06
Oh, right. Look, the idea is, nautilus showed the USB stick not mounted. Same directory as the cdrom (yep, /media). And the USB stick was unmounted is the point.

I'm not a n00b, I'm extremely sleep deprived after going through recovery and figuring out that gSpace will make a good backup solution.

---

### Post by MarinaraOfDeath on 2006-09-06
wpshooter, eventually I'd like to switch to linux only, but first I have to finish my degree since I have some software I need but I don't have access to except the windows versions.

I look forward to using only, though it remains to be seen if'n it'll be Fedora or Ubuntu.

---

### Post by MarinaraOfDeath on 2006-09-06
By the way, the aforementioned fsck****.** files were indeed mixtures of text files and binary. I've been copying the text and resaving. I've recovered quite a bit so far.

Again, thanks for y'alls help.

---

