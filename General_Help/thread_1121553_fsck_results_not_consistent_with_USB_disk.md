---
title: "fsck results not consistent with USB disk"
date: 2009-04-10
forum: General Help
---

### Post by skogsjanne on 2009-04-10
I have an external USB hard disk (1TB Samsung) that behave strange when I force a filesystem check on it. Sometimes fsck report errors, sometimes not.

The system is an AMD Athlon 64 3500+ on an Asus A8V motherboard. The filesystem on the USB disk is ext3.

Any clues?
TIA
/Janne

jan@maxim:~/Desktop$ uname -a
Linux maxim 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

root@maxim:/home/jan# fsck -f /dev/sdc1
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
Pass 1: Checking inodes, blocks, and sizes
Error reading block 90735050 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? yes

Force rewrite<y>? no

Error reading block 90735051 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? 

/dev/sdc1: e2fsck canceled.

root@maxim:/home/jan# fsck -f /dev/sdc1
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sdc1: 1844857/122109952 files (6.0% non-contiguous), 243594291/244190000 blocks

---

### Post by dcstar on 2009-04-10
> **skogsjanne said:**
> I have an external USB hard disk (1TB Samsung) that behave strange when I force a filesystem check on it. Sometimes fsck report errors, sometimes not.
........

And you make 100% sure you have unmounted it before running fsck?

---

### Post by lensman3 on 2009-04-11
dcstar's advice about umounting the device is very important.  Except I'm not sure where or how you would find the device if it is not mounted.

However, the work around is to mount the device as "read-only". Generally, "mount -o ro <device-name> <mount-point>".  "ro" is read only.

Recall that USB thumb drives are a strange device.  Because there are just some many writes to the hardware before the device "burns-out", the hardware does load-leveling so that no single memory area is written to too often.  This read-write behavior should be transparent, but fsck does some low level reads and writes so the errors could be "BS".

---

### Post by callie510 on 2009-04-11
The advice about thumb drives is interesting and I never knew that! But unless USB  thumb drives have come a long way since the last time I checked ebay, I'm pretty sure the OP's 1 terabyte drive is the traditional external type, probably 3.5" :)

Also, uhh, person above me, you "find" the drive by running "fsck /dev/hdc1" (in the OP's case)... locates the partition and drive without mounting it. Never mount before running fsck. I don't think this is a good idea, even read only.

Hmm. I would check the drive for errors or imminent failure. Sounds like you might have some bad sectors on that drive. Have you shaken it recently while it was spinning? I killed an old external in a cheap case that way. If your external drive supports SMART data (which most modern drives do - since yours is 1TB i bet it does), download a utility that can read that. 

Your drive's SMART data is a pretty cool thing to check out no matter what. You will learn some interesting things about your drive, like if it's had any recent errors, or how many times it has spun up and down in its lifetime. You can also learn that it is completely healthy, in which case your problem is something else. But my bet is on drive damage or mechanical failure.

---

### Post by skogsjanne on 2009-04-12
No cigar.
Can the reason for this be that it is connected to USB?
Both my other (SATA internal) disks pass the test.

I think the only way I have abused the disk is by storing offensive material on it. It's only slightly more than a year old so I thought it should be ok but maybe I should get a new one and copy all data to it before the disk crash and leave me with a disorganised backup :^)

/Janne

root@maxim:/home/jan# smartctl -a /dev/sdc
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Device: SAMSUNG  HD103UJ          Version: 
Device type: disk
Local Time is: Sun Apr 12 08:39:38 2009 CEST
Device does not support SMART

Error Counter logging not supported
Device does not support Self Test logging

root@maxim:/home/jan# smartctl --smart=on /dev/sdc
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

unable to fetch IEC (SMART) mode page [unsupported field in scsi command]
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
root@maxim:/home/jan#

---

