---
title: "Dell Mini 9 Ubuntu ?"
date: 2011-06-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by internetrush on 2011-06-16
Hello all, 

After windows XP took a dump (as all windows eventually do) on my dell mini 9 i decided to move on (finally) to Ubuntu. This is what XP showed at startup: 
> 
For Realtek RTL 8101E/8102E PCI-E Ethernet Controller V1.08 (080408)
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting PXE ROM
Operating system not found

Downloading and getting it onto the USB Drive was no trouble, however, once getting to the installation i get the following error: 

> 
input output error during write on /dev/sda 


Next error:

> 
Error fsyncing/closing /dev/sda: input/output error


After checking the bios to make sure its not the SSD it shows that i have a 7399MB drive in bios. 

I loaded up GParted Live and it was unable to create a partition table for the very reasons above. I'm guessing the drive is dead, any advice?

EDIT: 

After finding some more posts about downed drives, i tried to reset the first few bytes of the drive with a "dd if=/dev/zero of=/dev/sda" and then "sfdisk -s" just to get some basic info, both commands got the following problem

>  Permission Denied/ Cannot Open /dev/sda for reading 
I'm not very versed in Linux so i would appreciate as much explanation and command lingo as possible. 

Thanks!

---

### Post by mörgæs on 2011-06-16
Hi, welcome to the fora.

The note you posted shows that the computer is trying to boot from PXE. The settings in BIOS should be 1) USB, 2 ) SSD, 3) PXE.


From this post
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)
you can download Killdisk. Running Killdisk and erasing everything is will tell you if the SSD is dead.

---

