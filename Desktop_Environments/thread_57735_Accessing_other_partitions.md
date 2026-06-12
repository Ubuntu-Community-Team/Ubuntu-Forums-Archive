---
title: "Accessing other partitions"
date: 2005-08-17
forum: Desktop Environments
---

### Post by FrozenDice on 2005-08-17
I'm really new to Ubuntu after moving from slackware and can't seem to find out how to access my windows partition (dual boot).  On slack all the hard drives were listed under /mnt.  I'm trying to repare my windows install after I screwed it up previously trying to get gentoo to work and now have to replace the NTOSKRNL.EXE kernel.   So If I could just figure out how to access it I should be fine I think.   :roll:

---

### Post by mtelewicz on 2005-08-17
You need to manually mount the partition to a directory on your filesystem.  First, you need to figure out the device name for the partition you need to mount.  The pattern is this:

/dev/hdxy

Where "x" is a letter corresponding to the hard drive (a is primary master, b is secondary master, c is primary slave, etc.) and "y" is a number corresponding to the partition (first partition is 1, then 2, then 3, etc.).  Therefore, the first partition on your primary master hard drive would be:

/dev/hda1

Next, select a mount point.  I use /media/Windows.  You may have to make the directory.  Here's the mount command:

mount /dev/hda1 /media/Windows

Then change directory to /media/Windows and you should be looking at the contents of that hard drive.

One thing, though.  If your Windows partition is NTFS, you may have some problems writing to it.  Writing to NTFS isn't really supported....there are some hacks, but I've read that it is iffy.  Personally, I have a small hard drive dedicated to transfering data between my NTFS drive and my EXT3 drive which is actually FAT32. 

Hope this helped.

---

### Post by mtelewicz on 2005-08-17
You should also check out this link:

[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

---

