---
title: "partitioning help - merge re-size primary partition"
date: 2009-01-03
forum: General Help
---

### Post by jagman on 2009-01-03
Hi All

This is my PC:
Dell Dimension E521, AMD 64 X2 3800+ (2 Ghz), 4 GB DDR2 RAM (from Crucial), 40 GB SATA harddrive, SATA DVD/RW, ATI X1300 Pro 256MB, SATA 160 GB HDD

Setup:
Triple boot OS using Grub
WinXP
Ubuntu 8.04
BackTrack 3

Problem:
I have got all the 3 OS's above working and installed and managed booting with Grub.
In the process of installing them and partitioning etc I have no ended up with 50 GB of un-used (unallocated) HDD space.
I want to give this space to my windows C: partition

None of the tools I have tried will allow me to format and then merge or re-size the windows NTFS partition into the free space.  I think the problem is that I already have 4 primary partitions on the HDD.  What can I do?
(I would rather not delete my windows parititon and build a new one utilising all the free space).

The attached pictures show output from QTparted, fdisk and gparted

Thanks for reading

Jag

---

### Post by caljohnsmith on 2009-01-03
How about running gparted from the terminal of the Live CD (Applications > Accessories > Terminal) by doing:
```
gksudo gparted
```
And then click on your Windows partition, click on "resize/move", and see if gparted will let you resize it to use the unallocated space. If not, please post the messages that gparted prints in the terminal Window. That might give some clues.

---

### Post by Irony on 2009-01-03
You should be able to click on the ntfs partition then right click and resize - then drag the right side of the partition over as far as it will go, then apply.

If not then just format the unallocated partition as ntfs and it will show up as an extra drive in windows where you can store stuff. Note this may not then match your fdisk -l which will mean you will then have to relabel the fdisk for grub to work and then re-install grub.

---

### Post by rolnics on 2009-01-03
Is there any reason you want it as one Windows partition? When I had XP I always had a 15Gb primary partition (C: ) and then had other partitions such as a programs partition and a data one it supposedly help with fragmentation (de-frag a partition at a time) and helps with backing up. 

So my point is would it not be easier to just use this as another partition and make it a logical one if that's possible?

---

### Post by jagman on 2009-01-03
Thanks for the replies.

@ Rolnics & Irony - I cannot create a new partition and format it because I have already used/created 4 primary partitions.  I cannot make any more.  That is why I just want to resize the NTFS and use the unallocated space.
I'm not sure if I could've built the OS's, home folder and Swap disks diferently so that I only used 3 primary partitions?

@ caljohnsmith - I will try your idea - with the boot cd and post the results.  Thanks

Regards

Jag

---

### Post by Shpongle on 2009-01-03
id try to run gparted from the live cd, it worked for any partition issues i had:)

---

### Post by jagman on 2009-01-10
Thanks caljohnsmith and DillByrne

Running gparted from the live CD worked and allowed me to re-size the drive.  On reboot Windows did a drive integrity check and everything passed.

Ta

Jag

---

