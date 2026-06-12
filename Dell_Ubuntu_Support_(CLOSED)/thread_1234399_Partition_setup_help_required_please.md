---
title: "Partition setup help required please"
date: 2009-08-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by EvansFive on 2009-08-07
I have a new DELL desktop running Vista 64 Ultimate (8gb RAM).  I have set up dual boot on a Mac but I am new to the PC setup side of things.

I did a shrink on the C: drive to free up 29gb.  I was planning to put the linux swap file and the /boot partition on this drive.  Then put the remaining linux partitions on an external esata drive attached to the desktop.  I was planning to install 64bit Ubuntu.

BUT...

After I booted my ubuntu CD and ran gparted, it would only let me create the primary swap partition and not /boot...because it said I could only have 4 primary partitions (Vista is taking up the other 3).  It said I would have to create an extended partition!!!!

Based on this I have a few questions:
1) Can I create an extended partition to hold the linux swap and /boot?  If so how do I need to configure this please...some detailed instructions would be appreciated?  Is this supported for booting Ubuntu?

2) I am putting swap and /boot on the internal PC drive because I had to do something similar for the Mac setup...the Mac cannot boot Ubuntu from an external drive.  Do I need to do this for the PC side OR can I just setup all my partitions on the external esata drive?  Can I boot Ubuntu directly from an external esata drive?

Even if I shrink the internal C: drive further I am still not able to set up both a swap partition and a single linux partition because of the primary partition number limit.  I am back to this extended partition stuff and I guess I am concerned over whether this will work of not?

I need to keep Vista for other reasons but really wanted to install Ubuntu as I have become quite attached to it on my Mac!

Any help please would be gratefully received?

---

### Post by SoftwareExplorer on 2009-08-08
> **EvansFive said:**
> I have a new DELL desktop running Vista 64 Ultimate (8gb RAM).  I have set up dual boot on a Mac but I am new to the PC setup side of things.

I did a shrink on the C: drive to free up 29gb.  I was planning to put the linux swap file and the /boot partition on this drive.  Then put the remaining linux partitions on an external esata drive attached to the desktop.  I was planning to install 64bit Ubuntu.

BUT...

After I booted my ubuntu CD and ran gparted, it would only let me create the primary swap partition and not /boot...because it said I could only have 4 primary partitions (Vista is taking up the other 3).  It said I would have to create an extended partition!!!!

Based on this I have a few questions:
1) Can I create an extended partition to hold the linux swap and /boot?  If so how do I need to configure this please...some detailed instructions would be appreciated?  Is this supported for booting Ubuntu?
Linux Swap should be fine. I'm guessing that boot would work--I run my main os off of having / on an extended partition w/o a separte boot.

> **EvansFive said:**
> 2) I am putting swap and /boot on the internal PC drive because I had to do something similar for the Mac setup...the Mac cannot boot Ubuntu from an external drive.  Do I need to do this for the PC side OR can I just setup all my partitions on the external esata drive?  Can I boot Ubuntu directly from an external esata drive?
Probably would work, you might have to change a boot order setting in the BIOS or do some grub stuff. Take your pick and I'll see how much I can help.

---

