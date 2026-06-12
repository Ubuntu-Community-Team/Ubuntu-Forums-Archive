---
title: "Accessing 2nd hard drive with nautilus, and backing up data"
date: 2006-09-25
forum: Desktop Environments
---

### Post by Skippy_X on 2006-09-25
OK

I've got Breezy on a desktop pc. This computer has two hard disks, one set as master (which has ubuntu on it and my current working files), the other is a 20 Gig drive which I'd like to use to backup some of my directories regularly.

I've tried to access the 2nd drive via nautilus with no success. ](*,)  I know there are already some files on there, but I have no idea what is on it. Could be about anything.

Here's what I get when I "sudo fdisk -l"

_________________________________

Disk /dev/hdc: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device    Boot      Start         End      Blocks   Id  System
/dev/hdc1      *           1        7383    59303916   83  Linux
/dev/hdc2               7384        7476      747022+   5  Extended
/dev/hdc5               7384        7476      746991   82  Linux swap / Solaris

Disk /dev/hdd: 20.4 GB, 20491075584 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        2491    20008926   83  Linux

____________________________________

How do I get to this drive using nautilus to see what's on it?

Also...

I'm looking for a simple tool to backup some of my directories (mostly music files). I'd like to completely automate the process. Are there any *very* simple GUI tools that I could use to automatically backup specific directories to the 2nd drive?

---

