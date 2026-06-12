---
title: "Gparted NTFS resize problems"
date: 2005-12-01
forum: Desktop Environments
---

### Post by diddy_tong on 2005-12-01
I've been looking through the forums for the answer to this one, but haven't been able to find the same problem.

I have a laptop with a 20GB hard drive, with both Ubuntu 5.10 and Windows XP installed.  I'd like to shrink my Windows XP partition (NTFS), so I can create a FAT32 partition from which to share (read/write) files between Ubuntu and Windows.  

I've tried to use gparted to do this, but it gives me an error telling me that the partition is busy.  I have tried unmounting it, and also booting from a Live CD and doing it, but I still get the same error.  What's the best way of making sure the HD isn't being used so I can resize the partition?

---

### Post by aysiu on 2005-12-01
I know Azz is convinced [DiskDrake](http://qa.mandriva.com/twiki/bin/view/Main/DiskDrake) and GParted are the same, but they're not. I've run into problems like this (and read about problems like this) in QTParted and GParted all the time. I've never had this problem using DiskDrake.

I don't actually install Mandriva, but I use the first disk of the Mandriva installer all the way through repartitioning and resizing with DiskDrake, then I force a restart and ditch Mandriva.

---

### Post by az on 2005-12-02
I have never used DiskDrake.  I do not know what it can and cannot do.  I do know that Ubuntu provides the same tools.

Probably the live cd is mounting your swap partition from your Ubuntu install.  You can unmount that and you are good to go. 

sudo swapoff /dev/hda5

The installer does a great job of automagically detecting and resizing a windows partition.  It is just as straightforward as doing it with another utility, graphical or not.

---

### Post by meborc on 2005-12-02
welllllll ... i find the partitioning tool that comes with ubuntu a bit complicated one... it has big disadvantages as it is way to complicated for new users who just want to get the whole partitioning thing over and done with...

for example (if i remember correctly) if you run an fresh install, it asks you wether to proceed with suggested partitioning or to go to advenced mode... i, for one, was quite worried about the suggested partitioning and wanted to make sure, that what is going to be done with my hdd is the correct way... well... after about 5 minutes of trying to figure out what the program is telling me i lost my temp and dicided to go back and try the suggested install... as the advenced mode was too advenced for me... well... it was impossible to go back to the old selection... only thing i could do was to go back to the hardware detection and after that the normal partitioning screen was restored...

i don't know if i got the point, but the partitioning should be made more 'human'... and i know that this is not the first time it is said... but it is the first time for me to see DiskDrake (any relations to dapper perhaps?) and i like it... hope something like this will be implemented soon to prevent people to give up even before the adventure begins :)

---

### Post by az on 2005-12-02
The current Breezy installer is a little better than the one you describe.  You do not really need to know the intricacies of your hard disk partitions to make some room and get ubuntu on there safely.

And the next version of Ubuntu (Dapper) will (should) be live-cd based, so the partitioner will be graphical.

---

### Post by aysiu on 2005-12-02
Even though I tout the beauties of DiskDrake, I don't really recommend Mandriva overall. There are little bits and pieces of several distros that I really like. Mandriva happens to have an excellent partitioning tool.

But Ubuntu is an excellent distro. Nothing's stopping you from using Mandriva's partitioning tool and then using Ubuntu.

---

### Post by az on 2005-12-02
I'm not taking anything away from DiskDrake.  I never have user it.  

I do not even know if ntfsprogs is installed on the live cd.  If that is not the case, then Gparted on the live will not work out-of-the-box for this.  Also, the fact that the live cd will mount and use a swap partition prevents you from partitioning that disk if you do not know that you have to unmount it.

The only thing that could be a big problem with DiskDrake is that it is a big download for such a small application - especially since most users post with either an ubuntu install cd or both the live and install cd in-hand.

That's all.

---

