---
title: "Ubuntu will not load unless in Recovery Mode"
date: 2009-02-12
forum: General Help
---

### Post by Blue_Mercury on 2009-02-12
I'm not entirely sure what I've done to my OS, but I was screwing around with drive mounting and attempting to stop Ubuntu from auto mounting the windows partition into mnt/windows that I had previously instructed it to do so.  I had not realized when I set up this auto mount that ubuntu was already doing this under /host so I wanted to remove the duplicate I created.   It is possible that this isn't what caused my problem and could be a coincidence.

When I try to boot normally, the screen goes black like usual before the login screen, but just stays there.
When I boot into recovery mode it eventually says there was a failure and writes this in a log file in /var/log/fsck/checkfs

Log of fsck -C -R -A -a 
Thu Feb 12 18:21:31 2009

fsck 1.41.3 (12-Oct-2008)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda1: 85 files, 3969/20017 clusters
/dev/loop0 is mounted.  e2fsck: Cannot continue, aborting.


fsck died with exit status 8

Thu Feb 12 18:21:32 2009
----------------

I type in exit, a menu comes up with the option to boot normally.  I boot normally and Ubuntu works just fine.

What did I do, and how do I fix it?

---

### Post by dcstar on 2009-02-12
> **Blue_Mercury said:**
> I'm not entirely sure what I've done to my OS, but I was screwing around with drive mounting and attempting to stop Ubuntu from auto mounting the windows partition into mnt/windows that I had previously instructed it to do so.  I had not realized when I set up this auto mount that ubuntu was already doing this under /host so I wanted to remove the duplicate I created.   It is possible that this isn't what caused my problem and could be a coincidence.

When I try to boot normally, the screen goes black like usual before the login screen, but just stays there.
When I boot into recovery mode it eventually says there was a failure and writes this in a log file in /var/log/fsck/checkfs

Log of fsck -C -R -A -a 
Thu Feb 12 18:21:31 2009

fsck 1.41.3 (12-Oct-2008)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda1: 85 files, 3969/20017 clusters
/dev/loop0 is mounted.  e2fsck: Cannot continue, aborting.


fsck died with exit status 8

Thu Feb 12 18:21:32 2009
----------------

I type in exit, a menu comes up with the option to boot normally.  I boot normally and Ubuntu works just fine.

What did I do, and how do I fix it?

Post the contents of your /etc/fstab file.

---

### Post by Blue_Mercury on 2009-02-12
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
/dev/sda2	/host	ntfs	defaults,nls=utf8,umask=0222,nosuid,nodev	0	0
/dev/sda1	/media/DellUtility	vfat	defaults,utf8,umask=0	0	2
/dev/loop0	/media/loop0_	ext3	defaults	0	2
/host/ubuntu/disks/root.disk	/	ext3	loop,errors=remount-ro,relatime	0	1
/host/ubuntu/disks/boot	/boot	none	bind	0	0
/host/ubuntu/disks/swap.disk	none	swap	loop,sw	0	0

---

### Post by dcstar on 2009-02-12
> **Blue_Mercury said:**
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
/dev/sda2	/host	ntfs	defaults,nls=utf8,umask=0222,nosuid,nodev	0	0
/dev/sda1	/media/DellUtility	vfat	defaults,utf8,umask=0	0	2
/dev/loop0	/media/loop0_	ext3	defaults	0	**2**
/host/ubuntu/disks/root.disk	/	ext3	loop,errors=remount-ro,relatime	0	1
/host/ubuntu/disks/boot	/boot	none	bind	0	0
/host/ubuntu/disks/swap.disk	none	swap	loop,sw	0	0

Make that 0 and things should improve - why is it there anyway?

---

### Post by Blue_Mercury on 2009-02-12
Not sure, but it could have had something to do with either the NTFS Configuration Tool or, Disk Manager available in Add/Remove Applications

I didn't edit that partitions variables, I was removing a redundant /dev/sda2 auto mount

Knowing what file to look at helps

---

### Post by dcstar on 2009-02-12
> **Blue_Mercury said:**
> Not sure, but it could have had something to do with either the NTFS Configuration Tool or, Disk Manager available in Add/Remove Applications

I didn't edit that partitions variables, I was removing a redundant /dev/sda2 auto mount

Knowing what file to look at helps

That last digit sets a fsck on boot/mount, "1" should only be set for the root partition and "2" is for any other filesystem you want checked on boot-up.

If it is set for bogus/non-existent filesystems then you experience the problems you have been having.

---

### Post by Blue_Mercury on 2009-02-13
It worked, thanks.

---

