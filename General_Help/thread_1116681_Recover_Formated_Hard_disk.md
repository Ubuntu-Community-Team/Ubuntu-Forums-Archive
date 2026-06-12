---
title: "Recover Formated Hard disk"
date: 2009-04-05
forum: General Help
---

### Post by rawandnet on 2009-04-05
Hi all,

by mistake i formated my extermal USB hard dirve as linux partition, i had more than 300GB data storage on it. is there away to restore that data? My driver is the following

Disk /dev/sdh: 500.1 GB, 500107862016 bytes

255 heads, 63 sectors/track, 60801 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x44fdfe06



Device Boot Start End Blocks Id System

/dev/sdh1 * 1 510 4096543+ 82 Linux swap / Solaris

/dev/sdh2 511 60801 484287457+ 8e Linux LVM


thanks

---

### Post by callie510 on 2009-04-05
did you quick format or slow format? Quick formats are much easier to recover from.

---

### Post by rawandnet on 2009-04-05
White trying to install Ubuntu, by mistake I have deleted that driver and did quick format, but I haven't install the OS on the partition.  Does Linux command provides recover data or I have to use third party software?

thanks

---

### Post by callie510 on 2009-04-05
I recently recovered from a quick format and I hope your recovery is as easy as mine was :) Testdisk recovered my partitions after a quick format and everything was precisely the way it was before the format. 

Option 1: Do you have ubuntu installed somewhere? Install and run testdisk.

Option 2: If you don't have ubuntu installed, go here [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) and burn a boot CD. Boot onto it and run testdisk. I hope you can use this to see a usb hard drive. I can't check with my own CD for a few hours.

---

### Post by rawandnet on 2009-04-06
> **callie510 said:**
> I recently recovered from a quick format and I hope your recovery is as easy as mine was :) Testdisk recovered my partitions after a quick format and everything was precisely the way it was before the format. 

Option 1: Do you have ubuntu installed somewhere? Install and run testdisk.

Option 2: If you don't have ubuntu installed, go here [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) and burn a boot CD. Boot onto it and run testdisk. I hope you can use this to see a usb hard drive. I can't check with my own CD for a few hours.


Testdisk brought back my data, thank you so much for your help.

---

### Post by hyper_ch on 2009-04-06
restore the files from your backups.

---

