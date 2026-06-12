---
title: "Ubuntu 10.10 didnt install properly"
date: 2010-10-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by VertigoVII on 2010-10-18
Well i tried to install Ubuntu 10.10 onto my dell side by side with Windows 7 on my dell studio 1558.. and well, it crashed badly half way through making the partition, and its reserved some memory for Ubuntu (but not the full thing), so its blocked off 2ish GB of data for a partition which failed and i cant find it to delete it, so do you know where the file path is so i can delete it and then try again?

---

### Post by Hack.The.Pow. on 2010-10-18
try booting into Windows 7 and downloading Partition Wizard.  This should allow you to see all of your systems partitions and delete them.  

If you are going to try again though I would recommend partitioning off about 10GB of space to ensure you won't run into any problems.  With the size of todays drives I'm sure you can afford it.

---

### Post by VertigoVII on 2010-10-18
> **Hack.The.Pow. said:**
> try booting into Windows 7 and downloading Partition Wizard.  This should allow you to see all of your systems partitions and delete them.  

If you are going to try again though I would recommend partitioning off about 10GB of space to ensure you won't run into any problems.  With the size of todays drives I'm sure you can afford it.

I'll do that now, and yeah it set it to about 25GB before hand, so im not sure how it came up as a small amount taken up, if it was larger i could have found it under WinDitStat probably.

Thank you for the help and i will tell you how it goes

---

### Post by VertigoVII on 2010-10-18
Thank you very much for the advice! but i have one more question.

When Wiping the partition should i;
> Fill Sectors with Zero (Quick)
Fill Sector with One (Quick)
Fill Sectors with Zero & One (Slow)
DoD 5220.22-M (3 passes) (Very Slow)
DoD 5220.28-STD (7 Passes)(Very Slow)

---

### Post by Hack.The.Pow. on 2010-10-18
> **VertigoVII said:**
> Thank you very much for the advice! but i have one more question.

When Wiping the partition should i;

What software are you using to do this?  If it is Partition Wizard (or really any other partition manager worth using) it should have a simple delete button on top.  Simply highlight the partition you wanted to install on and hit delete.

---

### Post by Meliority on 2010-10-18
I had the same issue with my dell 1520, I wanted to play around with ubuntu (alongside windows for now) and it crashed while installing from a USB despite being allowed to take 26-27 GB for its partition. I tried running it again and it spent over 20 hours working on its install before I canned it, reformatted the partition and tried the windows installer (which can't seem to start the download as far as I can tell).
 
I would make sure the image file you're using isnt corrupt and be careful about how much you let it partition off percentage-wise as deleting partitions can be a pain iirc.

---

### Post by VertigoVII on 2010-10-19
Well its done more than that now.. i think its deleted the partition, but now Windows 7 wont load! 

Ive tried a recovery... wont work.
Ive tried a repair... wont work
Cant load in Safe mode or anything...

BUT i can still boot Ubuntu of a USB stick (its what im on now)

when i try to recover it comes up
> Failed to extract the file D;Programme Files (x86)/Adobe/Adobe Photoshop CS5/dvaui.dll

Error (0x80070057)and when i do a repair it comes up 
> Boot Critial File: d;WIndows/system32/drivers/fvevol.sys   is corrupt.and all of my files was in the C partition, so i think when i tried to delete the Ubuntu partition it changed the boot up to D, and not keeping it on C!!! how can i change it back to C? and i can only do it through BIOS, and nothing else. I looked and all i can change it from is Hard Drive to USB or DVD Drive, but not specific partitions...

HELP?!

---

