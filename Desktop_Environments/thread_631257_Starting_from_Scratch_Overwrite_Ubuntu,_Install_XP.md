---
title: "Starting from Scratch: Overwrite Ubuntu, Install XP"
date: 2007-12-04
forum: Desktop Environments
---

### Post by bdcheung on 2007-12-04
I've got Gutsy installed as the only OS on my laptop.  I want to re-install XP and then reload Gutsy to have a dual-boot system.  I'm encountering a problem reformatting, though: the Windows install CD cannot detect the hard drive.

I assume this is because the entire drive is formatted as ext3, and the Windows recovery CD can't read it.  What is the fix for this?  Thanks in advance!

- Brian

---

### Post by banewman on 2007-12-04
Put the livecd from ubuntu in and select "gparted" from the menu and delete and format the drive - then use the windows cd to make a partition for it but leave room for the ubuntu install. :)

---

### Post by bdcheung on 2007-12-04
> **banewman said:**
> Put the livecd from ubuntu in and select "gparted" from the menu and delete and format the drive - then use the windows cd to make a partition for it but leave room for the ubuntu install. :)

When, using the XP install CD, I create the partitions for Ubuntu, should I leave them unformatted?  thanks for the quick reply!

---

### Post by banewman on 2007-12-04
Just sort out the windows partition/s and leave the rest as free space - windows won't set up stuff for linux - they're unfriendly :)
Use the live cd for setting the ubuntu partitions :)

---

