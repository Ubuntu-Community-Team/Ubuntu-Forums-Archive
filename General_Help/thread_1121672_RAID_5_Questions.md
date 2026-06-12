---
title: "RAID 5 Questions"
date: 2009-04-10
forum: General Help
---

### Post by Seaweed on 2009-04-10
I've been reading about setting up RAID 5 in ubuntu using mdadm and I have some questions I haven't been able to find the answers to.

My situation is this, I have recently set up a home server using ubuntu, when I built it and set it all up I only bought one 1.5TB drive. This drive is currently partitioned as follows

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c0f91

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      181172  1455264058+  83  Linux
/dev/sda2          181173      182401     9871942+   5  Extended
/dev/sda5          181173      182401     9871911   82  Linux swap / Solaris


Now I have read about RAID 5 I naturally want to get an array set up for redundancy reasons. I had originally planned to buy an additional two 1.5TB drives and build an array using these and my existing drives.

I had planned this because I had been told by someone I would be able to keep the contents of my current drive when the array was built, however everything I have read regarding setting up a RAID 5 array in ubuntu contradicts this?

So assuming I do need to format all 3 drives my plan would be to buy 3 more drives instead of 2 and use these to create an array separate from my current drive. Once I have this array created how do I go about growing the array to include my existing drive without loosing my ubuntu installation and the ability to boot?

Any advice on how I can go about getting a RAID 5 array set up without having to loose the contents of my current 1.5TB drive would be great.

---

### Post by fjgaude on 2009-04-12
Maybe this link will help you in understanding some of the ins and outs of mdadm and growing:

[http://linux-raid.osdl.org/index.php/Growing](http://linux-raid.osdl.org/index.php/Growing)

So many things to consider, but do have a backup of important data.

---

### Post by Seaweed on 2009-04-13
My plans have changed slightly, I have read that it is not possible to boot to a RAID 5 array, I found some information on creating a /boot partition on all the drives in the array on a seperate RAID 1 array and leaving the rest of the file system on the RAID array to. However I couldn't find anything with enough depth to make me comfortable attempting it.

My plan is now as follows.

1. Order 3 additional 1.5 TB drives and create a RAID 5 array on these blank disks.
2. Copy my /home/ folder onto the new array 
3. Install an additional IDE drive and install a blank ubuntu installation onto this drive.
4. Boot to a live CD and copy my existing ubuntu installation from my current install onto this IDE drive.
5. Move my home folders location to the RAID 5 array using the instructions here [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
6. Format my current 1.5 TB drive and expand my RAID 5 array to include this drive


This seems to be my simplest option and also the most comfortable with which I am following. Once I have everything set up I plan to take regular backups of the IDE drive onto the RAID array incase this drive fails. My only current remaining uncertainties are as follows.

1. Will copying the entire contents of my 1.5TB drive to the fresh installation I plan to make on an IDE drive carry over all my existing applications and settings?
2. Can this be done from a Live CD I am assuming so?
3. When I am making regular backups of the IDE drive (I plan to use rsnapshot) what folders should I include to preserve all my applications and settings, I can backup the entire drive but it would be nice to save a bit of space in the process. 

Any relevant tutorial links to helping me achieve the above steps would be appreciated

---

### Post by fjgaude on 2009-04-13
> 1. Will copying the entire contents of my 1.5TB drive to the fresh installation I plan to make on an IDE drive carry over all my existing applications and settings?
2. Can this be done from a Live CD I am assuming so?
3. When I am making regular backups of the IDE drive (I plan to use rsnapshot) what folders should I include to preserve all my applications and settings, I can backup the entire drive but it would be nice to save a bit of space in the process.

1. If you do the copy correctly it will copy all settings, etc. Many folks use the **dd** command to do this kind of work. Although you likely can open two copies of Nautilus and drag and drop, one disk to the other.

2. I think so...

3. I don't know anything about **rsnapshot** but it might have ways to copy only certain folders. I would copy all to be on the safe side.

As philosophy you are going in the right direction... always have the boot drive separate from the rest of the important data. Always keep at least one backup of all important data. I use three, one online, one near-line, and one off-line. Everything I create needs to be saved; I'm a graphic designer.

Here's another link worth reading:

[http://www.hscripts.com/tutorials/linux-services/mdadm.html](http://www.hscripts.com/tutorials/linux-services/mdadm.html)

---

