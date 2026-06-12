---
title: "Disks manager not seeing newly created EXT3 partition correctly"
date: 2006-07-16
forum: Desktop Environments
---

### Post by radagast2 on 2006-07-16
I just ran into an odd problem.  I have two 120 gig hard drives in my computer, and up until today the second one had a lone 110GB NTFS partition on it (/dev/hdb1).  This partition was being mounted by Ubuntu. Today, using GParted in a 6.06 LiveCD, I deleted that partition and created two new primary partitions on that drive, the first was a 100GB EXT3 formatted partition (/dev/hdb1), and the second was a 10GB FAT32 (/dev/hdb2) partition.  

I then rebooted into my 6.06 install and attempted to use the disks manager to mount both partitions (to /bigshare and /fatshare, directories which I had already created).  While I could mount the FAT32 partition, the disks manager reported that the EXT3 partition had a format of NTFS, and it refused to "enable" it.  However, the partition is not NTFS, it's EXT3 (as I verified using QTParted).  

I've attached two screenshots that show what I'm talking about.

I'm guessing that I've done something wrong.  Any suggestions as to why this might be occurring (and how I can get my EXT3 partition mounted)?

---

### Post by radagast2 on 2006-07-17
I was able to get both partitions mounted by following Aysiu's guide ([http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)) and manually editing /etc/fstab.  

I still don't know why the disks manager was reporting the wrong filesystem, though ...

---

