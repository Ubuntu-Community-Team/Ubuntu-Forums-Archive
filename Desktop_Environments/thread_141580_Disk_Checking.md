---
title: "Disk Checking"
date: 2006-03-08
forum: Desktop Environments
---

### Post by TomAnthony on 2006-03-08
I just noticed that after every 30 disk mounts a disk check is scheduled. I was wondering how to do a disk check manually. Any ideas?

---

### Post by az on 2006-03-08
The *filesystem* is checked every 30 mounts.  It is checked with fsck.  You can change that with tune2fs.  You can also run an fsck manually, but the disk has to be unmounted - you do it from a ramdisk.

You can also look into badblocks.  It is part of the e2fs tools.  That checks your *disk* for badblocks.

man tune2fs
man fsck
man badblocks

---

### Post by tritium3 on 2006-03-08
This might be what I've been looking for. I will check it out, but here is my situation and why I am looking for a way to check all non-swap partitions in which I've installed ubuntu:

I installed ubuntu 5.10 on an external USB hard drive, into a single ext3 partition plus one Linux Swap partition. It was working great. Then I cloned these two partitions to a totally empty, second USB hard drive, using Acronis True Image 9.0 for Win-XP. Before ever even booting the second USB hard drive, I boot Ubuntu 5.10 Live CD, do an fsck on the ext3 partition on the second USB hard drive, and it comes up with numerous errors on the ext3 partition.

---

### Post by az on 2006-03-09
[QUOTE=tritium3]

 Then I cloned these two partitions to a totally empty, second USB hard drive, using Acronis True Image 9.0 for Win-XP. .[/QUOTE]

I would clone a partition using free-libre tools.  I would half-expect windows tools to not be able to handle linux partitions without some problems.  I think by far, people have had more success in copying linux partitions using GNU parted or partimage than other proprietairy tools.

---

### Post by tritium3 on 2006-03-09
Thanks, I'll take your advice. I did not know about free-libre tools, where can I find them please?

In the meantime, I've done some more testing and analysis, and it turns out the ext3 root partition was corrupt *before* I even cloned it with Acronis True Image 9.0 for Win-XP. I proved this by restoring it back to the *original* USB external hard drive, then booting the install disk with "rescue", then doing an "fcsk.ext3 /dev/sdx -n" on it. It showed as corrupt.

So, I've reinstalled Ubuntu 5.10 on the original USB external hard drive, and added the minimum stuff I don't want to have to re-do if the partition shows up as corrupted again, and have *not* made my first backup of the partition yet, until someone can help me with how to do a complete cold backup of any and all non-swap partition(s) into which Ubuntu was installed. Can you help with that? As I say, in the meantime I'll be looking at free-libre tools and GNU parted or partimage, as you suggested. Thanks in advance.

---

### Post by az on 2006-03-09
[QUOTE=tritium3]Thanks, I'll take your advice. I did not know about free-libre tools, where can I find them please?

In the meantime, I've done some more testing and analysis, and it turns out the ext3 root partition was corrupt *before* I even cloned it with Acronis True Image 9.0 for Win-XP. I proved this by restoring it back to the *original* USB external hard drive, then booting the install disk with "rescue", then doing an "fcsk.ext3 /dev/sdx -n" on it. It showed as corrupt.

So, I've reinstalled Ubuntu 5.10 on the original USB external hard drive, and added the minimum stuff I don't want to have to re-do if the partition shows up as corrupted again, and have *not* made my first backup of the partition yet, until someone can help me with how to do a complete cold backup of any and all non-swap partition(s) into which Ubuntu was installed. Can you help with that? As I say, in the meantime I'll be looking at free-libre tools and GNU parted or partimage, as you suggested. Thanks in advance.[/QUOTE]


By free-libre, I mean not proprietary.  Gnu parted and partimage are examples of software that can do what you need it to do and are licenced under the GPL (and are therefore free-libre).
 
The advantage of partimage is that it is simple.  It's dissadvantage is that it images an entire partition and not just the filesystem on it.  If you have old data there, it will be copied too.  So, if you have a 5 Gig partition of which only 2 gigs are taken up, you still can end up with a very large image,

Parted copied the filesystem.  So, if you want to transfer a 5 gig partition's 2 gig partition onto a 3 gig  partition, you can.  It is just a tad more complicated to use.

---

### Post by tritium3 on 2006-03-09
Thanks. In the meantime, I found the GParted LiveCD at:
[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")
and it looks like that may be what I need.

Thanks again.

---

### Post by az on 2006-03-09
[QUOTE=tritium3]Thanks. In the meantime, I found the GParted LiveCD at:
[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")
and it looks like that may be what I need.

Thanks again.[/QUOTE]
Gparted is a frontend to parted (it uses parted to do the actual work).  It should work just fine.

---

### Post by tritium3 on 2006-03-09
[QUOTE=azz] ...  You can also run an fsck manually, but the disk has to be unmounted - you do it from a ramdisk.[/QUOTE]

azz:
Could you provide either your own, or a good link to, a "howto" for running in a ramdisk, so that a ubuntu user can do an fsck manually on any or all of his non-swap partitions into which ubuntu is installed?
Thanks *very* much in advance.

---

### Post by tritium3 on 2006-03-10
I found that when I deleted the partitions using MS Windows, then recreated them with the GParted Live CD, the ext3 partition no longer became corrupted by Acronis True Image 9.0 for Windows. As well, I can use the Acronis Recovery CD to make backup images of the ext3 partitions. So neither Acronis nor Windows were the cause of my ext3 partitions getting corrupted, although I remain completely baffled as to why deleting all of the hard disk partitions with the Windows "Disk Management" gui would have cleared up the problem.

---

### Post by az on 2006-03-10
[QUOTE=tritium3]I think we can put this one to rest. I think I've found the fundamental culprit. After a *lot* more testing, I've determined that the filesystem gets corrupted by Acronis True Image 9.0 when Acronis takes a *backup* of the partition! And since I have no idea whether the corruption is copied onto the backup image itself, I am abandoning my efforts to image the partition with Acronis.
Thanks again for your help.[/QUOTE]

I'll chalk that up as another bad experience with proprietary partitioning tools.

Any live cd runs from a ramdisk.  The gparted live cd is one.  The ubuntu installation cd is another example.

You can boot the installer, let it go a few steps until it load the extra compenents (it installs the tools onto the ramdisk) and the you can go to a chell by hitting CTRL-ALT-F2.

The installed tools include all the parted tools and extentions as well as fdisk, and the extfstools.  So you can run fsck from that shell.  You can also boot the gparted live cd and run fsck from a terminal in it.

---

