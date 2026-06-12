---
title: "Recovering &quot;lost&quot; partition"
date: 2010-05-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Stoker580 on 2010-05-13
Here's the story so far.

When I installed version 10.4 on my Dell Inspiron 8500 the 60Gb hard drive was repartitioned into two, one for Windows XP Home Edition of 40Gb and one for Ubuntu of 20Gb. I then discovered that there was a problem with version 10.4 and decided to remove it and install an earlier version. Using Windows disc manager I deleted the 20Gb partition and fixed the MBR. I can now boot into Windows XP and see that it still has the 40Gb partition but when I go to install Ubuntu 8.10 it doesn't see anything and wants to take the whole 60Gb as one partition.

Although I intend to get rid of Windows ultimately I would prefer to have a dual boot arrangement where I can run either Windows or Ubuntu.

I guess that I need to reconnect the 2 oartitions that I now have into one. I have tried to extend the Windows partition using Disc Manager but when I right click on it  there is no option to extend available.

I'm completely new to Ubuntu and would appreciate any help.

---

### Post by wojox on 2010-05-13
Can't you click on manual partition?

---

### Post by Stoker580 on 2010-05-13
Yes I've tried that but I don't seem to be able to change anything. It just shows one partition of 60 Gb as if the Windows Partition doesn't exist. Being completely new to this I don't want to risk screwing it up completely.

---

### Post by gbrainin on 2010-05-13
For starters, let's see what your partition table looks like.  Boot off the live CD, open a terminal, and use the following command:
```
sudo fdisk -l
```
Then post the output of that command back here.

FYI, the fdisk command is for manipulating your partition table, but the -l switch means to just list what is currently there, without making any changes.

---

### Post by Stoker580 on 2010-05-13
Hi apologies for not replying sooner. Here is the output from fdsik

omitting empty partition (5)

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x43e243e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        5292    42462071    7  HPFS/NTFS
/dev/sda3            5292        7296    16101376+   5  Extended
/dev/sda5   ?      214580      278327   512053320   8b  Unknown


Many thanks for your help

---

### Post by gbrainin on 2010-05-13
Interesting.  I'm not sure why the installation program won't see the partition table the way fdisk does.  Any particular reason you're trying to install 8.10 instead of one of the more recent versions?  I'm wondering if it's something unique to that version.

---

### Post by Stoker580 on 2010-05-14
Well I started off trying 10.04 and had problems with the graphics - the pointer had a ghost or shadow and other graphic features were not right although plain text was OK. I then read that someone had installed 8.10 successfully so I tried that from the live CD and then discovered the problem with partitioning as described in my original post. Subsequently I have downloaded 9.10 and tried it from the livecd and have found that it is even better then 8.10 and so would be keen to instal it but the same problem exists with the partitioning. The installation partitioner does not recognise that there is another os (i.e. Windows XP Home Edition)  already installed and only provides me with the option of installing on a single 60Gb partition (i.e. 100% of the hard drive). The manual partitioning option doesn't seem to allow me to change that. Maybe it's because of my lack of experience with Ubuntu but I'm not sure how the manual partitioning option is supposed to work. How is it possible to change what is being displayed? I've tried clicking on the graphic bar that is displayed which represents the partition but nothing happens.

---

### Post by Stoker580 on 2010-05-14
Hi gbrainin

I've just decided to forget about retaining Windows XP. I've copied off any data that I might want and I've started the installation of Ubuntu 9.10 using all the hard drive.

Many thanks for your help.

---

### Post by gbrainin on 2010-05-14
Sorry I didn't catch you in time.  It's difficult to talk about the partitioner in the installation program, since the GUI has changed from one version to the next (though the function is basically the same) and I am going from memory.

However, if the fdisk program is capable of recognizing the two different partitions, it should be possible to manipulate them directly from the command line using the fdisk program.  My guess is that if you had manually deleted the extra partition, then the install program would have recognized it correctly.  However, many people are quite reasonably uncomfortable messing about with their partition tables, so I was looking for a different method before I suggested that.

If you decide you want to dual-boot after all, there are several good tutorials on the subject around on the internet.  Just be sure you find one that refers to the right version of Windows.  But if you're like me, you won't miss Windows enough to bother.  Good luck, and enjoy Ubuntu!

---

### Post by Stoker580 on 2010-05-14
The installation is done and dusted - only took a fraction of the time that version 10.4 took. I'm using the machine now. Just to try setting up a printer and mobile internet.

I don't think I'm going to miss Windows at all. The machine now boots in about 1 min and shuts down very quickly as well whereas with Windows... I'll say no more.

All the best and once again thanks for your help.

---

