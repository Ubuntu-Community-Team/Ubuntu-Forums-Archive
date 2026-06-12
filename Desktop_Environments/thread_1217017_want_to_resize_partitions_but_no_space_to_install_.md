---
title: "want to resize partitions but no space to install gparted!"
date: 2009-07-19
forum: Desktop Environments
---

### Post by chiangs on 2009-07-19
Hi all
I want to resize my partitions because there is no more diskspace. I read somewhere that I would need to install gparted but this came up in the terminal:

machiang@machiang-laptop:~$ sudo apt-get install gparted
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  xfsprogs reiser4progs jfsutils ntfsprogs
The following NEW packages will be installed:
  gparted
0 upgraded, 1 newly installed, 0 to remove and 169 not upgraded.
Need to get 879kB of archives.
After this operation, 3621kB of additional disk space will be used.
Get:1 [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) jaunty/main gparted 0.4.3-0ubuntu1 [879kB]
Fetched 879kB in 4s (206kB/s)                          
Selecting previously deselected package gparted.
(Reading database ... 102894 files and directories currently installed.)
Unpacking gparted (from .../gparted_0.4.3-0ubuntu1_i386.deb) ...
Processing triggers for man-db ...
/usr/bin/mandb: can't write to /var/cache/man/7775: [B]No space left on device
[/B]Setting up gparted (0.4.3-0ubuntu1) ...

This is what my hd looks like at the moment

machiang@machiang-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18543   148946616    7  HPFS/NTFS
/dev/sda2           18870       19457     4717440   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.
/dev/sda3           18544       18869     2618595    5  Extended
/dev/sda5           18544       18848     2449881   83  Linux
/dev/sda6           18849       18869      168651   82  Linux swap / Solaris

Partition table entries are not in disk order
machiang@machiang-laptop:~$ 

so basically, I want to resize my ubuntu partition to allow more space but there's no space to install gparted. I'm completely new to Linux so any help would be appreciated T_T

---

### Post by andrea000 on 2009-07-19
are you dual booting there is a way to do it but i would
just copy over the ubuntu partition with the windows 
partition then run the ubuntu cd and re install ubuntu
it may make it a little easier to do.The problem is that
ubuntu puts its self at the start on the partition so 
your going to have to move all that to the start after you
resize.You could use the entire drive for ubuntu then use
virtual box to install windows.Bu use the live cd if your
going to resize the partition makes having to un mount a
easier.

---

### Post by merlinus on 2009-07-19
First of all, this guide may help you to free up space:

[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

Also, you can use gparted live to work with partitions.  Download the .iso, burn it to a cd, and boot from it.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by ugm6hr on 2009-07-19
> **chiangs said:**
> so basically, I want to resize my ubuntu partition to allow more space but there's no space to install gparted. 

You do not need to install gparted at all.  In fact, that will not help at all.

You need to boot from a **Live CD** (e.g. Ubuntu or GParted Live) and run GParted from there.

---

