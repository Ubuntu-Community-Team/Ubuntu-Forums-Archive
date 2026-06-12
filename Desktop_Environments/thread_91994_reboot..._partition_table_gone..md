---
title: "reboot... partition table gone."
date: 2005-11-18
forum: Desktop Environments
---

### Post by Swad on 2005-11-18
I rebooted my laptop before I left work last night.  Everything had been working just peachy.  I came in this morning and it was stuck not seeing any operating system at all.  I booted a few live CDs (knoppix and ubuntu) and have had no luck mounting the root partition on the disk.  Well after looking at qtparted, it appears there is no partition tables.  It's like it was wiped out.

Anyway, is there some recovery software for ext3 to see if I can recover any data on that hard disk?  It's a laptop, so I guess I'm going to have to do this from a live environment.  I can't mount the disk and I'm not sure if it's even good anymore--the hardware may be failing.

---

### Post by Efwis on 2005-11-18
> Well after looking at qtparted, it appears there is no partition tables. It's like it was wiped out.

if it was wiped out, ie reformatted, you may not be able to recover anything from the disk.

you might want to look here to see if you can recover it though.
[http://www.data-recovery-software.net/Linux_Recovery.shtml](http://www.data-recovery-software.net/Linux_Recovery.shtml)

EDIT: [color=red]Note this has to be used on a Windows installation to work[/color]

---

### Post by Swad on 2005-11-18
I don't think it was actually formatted--I think just the partition table got trashed.  I'll take a look at the link.  Thanks.

---

### Post by Efwis on 2005-11-18
I was only using the reformatted comment as an example. not meaning that that was what had happened. 

although unless your laptop was locked up doesn' t mean somebody might have accidently done that. ya never know. :)

---

### Post by kalin on 2005-11-18
It's not all lost yet, take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=87562](http://ubuntuforums.org/showthread.php?t=87562)

I would recommend trying out the "testdisk" utility.

---

### Post by az on 2005-11-18
I have not used testdisk, but it looks like what you need.  I have used parted, though. 

Parted can recover lost partitions, too

Quote parted documentation:

2.4.12 rescue


Command: rescue start end 
rescue a lost partition that used to be about start and end 
Looks for file system signatures around start and end. If one is found, it will ask you if you want to create a partition for it. This is useful if you accidently deleted a partition with parted's rm command, for example. 

Example: 

(parted) print
Disk geometry for /dev/hdc: 0.000-8063.507 megabytes
Disk label type: msdos
Minor    Start       End     Type      Filesystem  Flags
1          0.031   8056.032  primary   ext3
(parted) rm
Partition number? 1
(parted) print
Disk geometry for /dev/hdc: 0.000-8063.507 megabytes
Disk label type: msdos
Minor    Start       End     Type      Filesystem  Flags

OUCH! We deleted our ext3 partition!!! Parted comes to the rescue... 

(parted) rescue
Start? 0
End? 8056
Information: A ext3 primary partition was found at 0.031Mb ->
8056.030Mb.  Do you want to add it to the partition table?
Yes/No/Cancel? y
(parted) print
Disk geometry for /dev/hdc: 0.000-8063.507 megabytes
Disk label type: msdos
Minor    Start       End     Type      Filesystem  Flags
1          0.031   8056.032  primary   ext3

It's back! :)

---

### Post by poptones on 2005-11-18
did you try fdisk to see if the disk is even accessible?

fdisk -l /dev/hda

if the drive is failing it should return some sort of error. Did qtparted report no problems? no clicking?

---

