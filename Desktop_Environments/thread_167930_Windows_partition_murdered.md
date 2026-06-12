---
title: "Windows partition murdered"
date: 2006-04-29
forum: Desktop Environments
---

### Post by john_spiral on 2006-04-29
Hi,

I've gone and trashed my windows XP partiton hda1 (FAT) attempting to resize it using [parted]("http://www.gnu.org/software/parted/") from a linux boot floppy, my laptop has no CD-ROM drive.

I attempted to expand hda1 into and over hda2 (ext2 old linux partition) making hda1 bigger.

WHAT WAS I THINKING, IF IT AINT BROKE DON'T FIX IT!!!!

When I boot XP I get the following error:

[B]Windows could not start because the following file is missing or corrupt:

<Windows root>\system32\ntoskrnl.exe.
Please re-install a copy of the above file.[/B]

Looks like the FAT on the partition has gone tummy up. I've attempted to use 
fsck (sudo fsck -t vfat -V -y /dev/hda1) from the prompt (booting ubuntu from hda3) but it takes forever trying to resurrect the files.

fsck spits out something similar for each file:

File size is bla bla...,  cluster chain length is > bla bla bytes.
Truncating file to bla bla.

This goes on forever, hda1 is only 6.3 gigs. 

any help will be super appreciated.

John

---

