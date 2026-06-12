---
title: "Clone Win98 drive with Ubuntu"
date: 2009-01-05
forum: General Help
---

### Post by msfisher on 2009-01-05
As can be seen from my other posts, I'm not completely shifted from Win98 to Ubuntu.  Unfortunately, my 80gig WD Win98 drive is dying.  Two different S.M.A.R.T. utilities warn me to replace it. It's also my hda with Grub in the MBR. I'd like to clone/copy/mirror the dying drive to an 80gig Maxtor I have on hand.  It's not in the best of condition (one of the utilities that reports my hda as 0% healthy reports this one as 96% and my Linux drive as 100%.  Linux comes out on top in this one!)

Also as my previous posts will show, though I can and do use the command line (I cut my teeth on MS & DR DOS), I prefer something visual.  I've used PowerQuest/Symantec DriveCopy in the past, but can't find the disks or the serial number.

Are there any Linux utilities to do the cloning?  I know I can use dd, but I'm not sure if my disks are exactly the same size (the Maxtor may be functionally slightly smaller).  I also know there may be something in Ubuntu, but I haven't looked yet (that's next on my to do list after I get my son from a friend's house).

Many thanks in advance!

---

### Post by beattyml1 on 2009-01-05
Have you tried using gparted with a live cd to copy your old win98 partition to unallocated space on your new drive

to do so run the live cd and boot into ubuntu

go to system->administration->partition editor
select your old win98 drive in the upper right hand corner
then select your win98 partition in the main list of partitions
click copy
select your new drive 
find a block of unallocated space that is large enough for the win98 partition

I am not sure whether or not this should work but I know that it will in every way duplicate your previous partition

---

### Post by bumanie on 2009-01-05
Gparted does copy partitions well - I prefer dd commands. To clone a hard drive with dd > sudo dd if=/dev/sda of=/dev/sdbThat is assuming that your win98 HDD is sda and that the 'new' HDD is sdb, if not you will have to change the drive names appropriately. This can be done via an ubuntu live cd. Other options are clonzilla or partimage, both GUI tools.

---

