---
title: "HDD space"
date: 2009-04-19
forum: General Help
---

### Post by RandomP on 2009-04-19
I have Ubuntu 8.10 that I got yesterday and installed it today on my desktop. I installed it from the live CD. I partitioned my hard drive for it to use up to about 22GB. Well, when I look at my hard drive stats it says that 28.4GB are used up and there is 172GB of free space. Total amount of space is 200GB. 

When I was setting up the partitions I made it so that the main partition which had Windows XP was 200GB big and the filled amount of space was 28.4GB/200GB. Where can I find the Linux partition that I made? In Windows, it is not listed as a drive under Start>My Computer. 

Here's what Ubuntu says:
[IMG]http://i190.photobucket.com/albums/z314/Shades14/PrimaryC.jpg[/IMG]

Here's what Windows XP says:
[IMG]http://i190.photobucket.com/albums/z314/Shades14/primary2.jpg[/IMG]

The math:
200GB Total according to XP and Ubuntu.
+
5.38GB XP Recovery partition on the Primary drive.
-----------
= about 206GB This drive should have around 238GB total (that is what it was when I first installed it). 

This would mean that the partition for Ubuntu is not counted here because then the count would be around 228GB. I would still be missing 10GB or so. If that is true, then does Ubuntu have a recovery partition that takes up space outside of the partition that I allowed it when I first installed it? Thanks! :grin:




-RandomP.

---

### Post by Vadi on 2009-04-19
It does reserve 5% space for emergency cases, but I think that takes account the partitition.

Install [GParted]("apt:gparted"), and go to system - administration - partition editor. That'll show all partitions more clearly.

---

### Post by RandomP on 2009-04-19
> **Vadi said:**
> It does reserve 5% space for emergency cases, but I think that takes account the partitition.

Install [GParted]("apt:gparted"), and go to system - administration - partition editor. That'll show all partitions more clearly.
Thanks for the reply and the download link.

Here is what it says:
[IMG]http://i190.photobucket.com/albums/z314/Shades14/Gpart1.jpg[/IMG]

I can see all of the partitions now. I am guessing those last three entries are for Ubuntu, am I right?:D

---

### Post by codeseer on 2009-04-19
Yep.

---

### Post by RandomP on 2009-04-19
Thanks. 

Another question, but this one is not really that important, can I make the partition that Ubuntu is on bigger?

---

### Post by Monotoko on 2009-04-19
Yes you can, youd need ntfsprogs from aptitude. That will then allow youto shrink your Windows partition and increase the size of your ubuntu partition.

---

### Post by Sidewinder1 on 2009-04-19
Yes, but you'd have to shrink the NTFS partition first, Gparted will do that for you. Make sure you defragment the NTFS prior to shrinking it.
HTH Side

---

### Post by jakupl on 2009-04-19
> **RandomP said:**
> Thanks. 

Another question, but this one is not really that important, can I make the partition that Ubuntu is on bigger?

you will need the [gparted live cd]("http://sourceforge.net/project/downloading.php?group_id=115843&filename=gparted-live-0.4.3-2.iso&a=77650553"), as you cannot change a partition that you are allready sitting on.

---

### Post by CatKiller on 2009-04-19
Or the Ubuntu install cd. That has GParted on, too.

---

