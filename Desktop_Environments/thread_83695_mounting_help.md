---
title: "mounting help"
date: 2005-10-29
forum: Desktop Environments
---

### Post by Snitz on 2005-10-29
I have 2 HDD's
1st: drive C (Fat) which I resized using P.M. and made a partition for ubuntu
2nd: drive F (Ntfs)

I want to mount these 2 drives (hdds) to be able to see them on ubuntu!!!

I have tried what they wrote on the guide site but it didn't work
can anyone help plz!

---

### Post by Xian on 2005-10-29
This forum is only for posting How-To guides.
Please post in the [proper](http://www.ubuntuforums.org/forumdisplay.php?f=91) section.

---

### Post by dbott67 on 2005-10-29
You'll have to determine what device (hda, hdb, etc.) has been assigned to each hard drive.  After that, you'll need to figure out which partition (hda1, hda2, hdb1, hdb2, etc.) each OS is on.

The easiest way is to install the graphical partition manager, gparted.  Open Synaptic and download it.

It will show you the device name (i.e. /dev/hda) as well as the partition numbers (i.e. hda1) for each drive & operating system.

From there, just follow the instructions on how to mount FAT and NTFS partitions here:
[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

Keep in mind that you'll have to replace the "hda1" shown in the example with the actual device & partition information for your computer.

-Dave

---

### Post by Snitz on 2005-10-29
merci Dave :D

---

