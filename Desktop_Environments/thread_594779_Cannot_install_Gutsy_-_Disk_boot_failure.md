---
title: "Cannot install Gutsy - Disk boot failure"
date: 2007-10-28
forum: Desktop Environments
---

### Post by Proffan on 2007-10-28
Hello,

I have the following hardware setup:

MB Abit IP35 Pro
Intel Core 2 Quad Q6600
2 GB RAM
5 SATA 320GB hard disks
1 SATA DVD drive, Samsung SH-S203B
1 IDE 320 GB hard disk

The first four SATA drives are configured as a RAID10 array, and contains my
Windows XP installation & user files. I want to install Ubuntu on the IDE disk,
so I burned the alternate desktop CD, in order to be sure to avoid writing
(and destroying) my RAID10 array.

I checked the downloaded ISO with winmd5sum, and burned it twice. The file
structure on the CDs look perfectly OK.

However, when I boot the computer, go into BIOS and change the boot order to
boot from the DVD drive, and then reboot, I get the error message:

DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER

The DVD drive has worked fine as far as I can tell, it has read all disks and burned
both CD's, DVD's and dual layer DVD's. The formware is the most recent.

Any suggestions?

---

### Post by byrneda on 2008-01-10
> DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER

This is the standard error message from your computer when it can't boot from a hard drive - I'm presuming this is from your IDE hard drive and not your RAID setup.
This is to be expected.

The real problem here is that you can't boot from your SATA DVD Drive.
Have you ever booted up from it before?
Try an OEM CD of W$ndows or some other media that is known to be bootable.

Other than that, take the newly burnt CD and bring it to another computer.
Does it boot there?  If so, your DVD is faulty, otherwise, the CD is faulty.

Can't really be anything else, unless your computer can't see your SATA DVD drive on bootup.

---

