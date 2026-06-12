---
title: "recovering lost partitions"
date: 2006-09-05
forum: Desktop Environments
---

### Post by elemental666 on 2006-09-05
I think I might be out of luck, however I thought I'd ask before I formatted this drive.  I inadvertantly deleted the partion off my external backup drive while reinstalling windows on another machine.  The drive did not get formatted, just blew the partitions away.  I am wondering if there is anyway to recover the data off this drive?  Its got a lot of stuff I really don't want to loose on it...

Before the blunder it was an ext3 partition.
The drive was connected to the laptop and when the winxp setup screen came up I accidentally deleted the partitions off the external, then I quit the setup thinking maybe the changes didn't get written.
But they did.

So the data should still be on the disk, but the partition tables are gone.

Hope that is clear, any help would be appreciated...

---

### Post by chicken101 on 2006-09-05
Well, if the partition table is gone, I'm not sure you'll be able to mount it.  I guess you could boot up the live cd, and see if the disk manager even detects it.  Usually to repartition a drive, it has to reformat it too.  But if there is no partition, you aren't going to be able to read anything. 

If it can mount the drive, try copying the contents on the drive to a cd or dvd.  You might be able to get your data back.

This is a tough one!  Hope this helps.:-k

---

### Post by elemental666 on 2006-09-05
The partition table is gone, so the /dev/sda device is there, but there is no partition to mount.  I can create a new partition on it, but I want to try to recover the old one.

---

### Post by Clouseau__ on 2006-09-05
Hi,

Maybe you should check [this guide]("http://servers.linux.com/article.pl?sid=06/08/21/1558230&from=rss"). 

[TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") apparently does a fine job recovering lost partitions. From the article:

> TestDisk can recover lost partitions of virtually any filesystem. PhotoRec can recover files of most types, including most picture and video formats. PhotoRec can be used on existing partitions, or can be used to recover files on deleted partitions without having to recover the underlying partitions. Both PhotoRec and TestDisk can be run on DOS, Windows (9x, NT, 2000, XP, 2003), Linux, FreeBSD, NetBSD, OpenBSD, Sun Solaris, and Mac OS X, and, their developers claim, can be compiled and run on most Unix systems.

Haven't (thankfully) had a chance to try it, but I hope it works for you.

Good luck! 

Clouseau__

---

### Post by elemental666 on 2006-09-07
Looks promising, will try it out report back, thanks

---

### Post by elemental666 on 2006-09-07
TestDisk for the win!

Thanks a million Clouseau__, 160GB worth of media and back ups saved!:-D :-D \\:D/ 

I'd give ya cookie if I could!

---

### Post by Clouseau__ on 2006-09-07
elemental,

Anytime! :) 

So glad I could help!

Clouseau__

---

