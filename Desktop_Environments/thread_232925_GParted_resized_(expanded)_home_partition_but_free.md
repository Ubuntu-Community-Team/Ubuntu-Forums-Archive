---
title: "GParted resized (expanded) /home partition but free space the same?"
date: 2006-08-09
forum: Desktop Environments
---

### Post by Robor on 2006-08-09
I had a 60GB drive in my Ubuntu/WinXP dual boot system that I cloned to an 80GB drive a while back.  I had the following partitions

/boot (100MB)
WinXP (40GB)
/ (8GB)
/home (12GB)
/swap (512MB)
Unallocated (20GB)

I booted the Ubuntu 6.06 LiveCD and ran GParted.  I moved the 512MB /swap partion to the end of the disk using some of the unallocated space and expanded it to 1GB.  That worked fine.  I then resized (expanded) the /home partition to use up all of the unallocated space from the end of the current /home partition to the beginning of the /swap partition.  My /home directory was about 12GB of 12.5GB full.  The resize worked showing a 32GB /home partition but the free space stayed the same (still only 500MB free).  Any ideas?

---

### Post by tagra123 on 2006-08-09
use resize2fs

[http://www.linuxcommand.org/man_pages/resize2fs8.html](http://www.linuxcommand.org/man_pages/resize2fs8.html)

After increasing the partion size resize2fs will grow the filesystem to fill the partition.

Used it on both my home and root partition without any problems.

---

### Post by etank on 2006-08-09
I'm going to have to remember that command. Seems like it could come in very handy someday.

---

### Post by Robor on 2006-08-09
**Thanks tagra123!**

I had to use a LiveCD and manually mount the partition I was resizing because it would be busy (in use) if I tried to resize from within my Ubuntu bootup.  The partition I extended was partition /dev/hda5 so in my case it was:

sudo e2fsck -f /dev/hda5 (to check for errors - I was prompted to do this when I tried the command below first)

then

sudo resize2fs -p /dev/hda5 (the -p switch isn't necessary - just gives progress)

Hope that helps someone else!

---

