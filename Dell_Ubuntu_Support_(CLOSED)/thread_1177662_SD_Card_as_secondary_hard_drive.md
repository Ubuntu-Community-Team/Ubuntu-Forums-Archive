---
title: "SD Card as secondary hard drive"
date: 2009-06-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by killerdragon on 2009-06-03
I had bought a 16GB SD card for my Dell Mini 9. I originally had it working with the Dell shipped version of Ubuntu. But, I wanted Xubuntu installed instead of the Dell version. So, I reformatted the SSD with ext3 and everything was working fine.
The reason for the SD card is that I would take some of the bigger folders, copy them to the SD card and create a symbolic link back to the SD card. However, after unwisely choosing some directories to be copied over, it seems my Dell mini 9 will not suspend.

If I have the SD card in on boot, and close the lid I get a blinking underscore character. If I have it in, but take it out before I tell the system to suspend, it will suspend, but only that one time. Any other attempt to suspend the computer will just "lock" the screen. If I leave the SD card out it will suspend just fine.

After looking through dmesg it seems like Linux wants to do some I/O to the SD after I yank it, probably due to the ext3 FS on it (Note: I removed all symbolic links to the SD card as hopes that would all the device to suspend, no dice). My question is what FS is better for my situation, I am thinking FAT32 but I am unsure.

---

### Post by coffeeaddict22 on 2009-06-03
Hi,
I'm not a filesystem guru, but you seem to want to essentially flush the disc buffer.  Any journalled filesystem is likely to run into the same problem.
Easiest way would be to manually unmount it before you suspend; You could write a script that runs on suspend to do the dirty work for you, although if you've got the OS on the card you'll be pushing your luck.

---

### Post by crewkid89 on 2009-06-04
this might have something to do with it a bug involving suspend in 9.04 with the sd reader. [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/272557](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/272557)

---

