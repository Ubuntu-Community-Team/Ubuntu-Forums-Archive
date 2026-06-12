---
title: "Resizing Partition"
date: 2006-08-19
forum: Desktop Environments
---

### Post by technel on 2006-08-19
Hello,

I have a 160gb Western Digital (eek) hard drive with two main hard drives (plus swap, even though I have 2gb of RAM). It is set up like so:

Windows partition (100gb) (NTFS)
Ubuntu partition (50gb) (ext3)
Swap partition (1gb) (SWAP) (yes, I know)

Now Ubuntu has only 3gb available and the Windows partition has 83 gb available. The problem, from what I have read, is that while the Windows partition can be resized, the Ubuntu partition would have to be completely moved to a new starting point.

As such, apparently gParted and the others relying on Linux partition program (the name slipped my mind, I believe qtParted and kParted uses it, or something like that). I tried Partition Magic 8 on Windows to see if it could do it for me and it just says "BAD" for the disk :\.

Any ideas?

---

### Post by meng on 2006-08-19
Better not rely on my advice alone when it comes to partitioning, but I thought it is a good time for you to consider this idea:
Since you're on the verge of reconfiguring the partitions, why not use a separate /home partition? Possibly most of your Ubuntu partition is taken up with files in /home anyway, unless you've a jillion applications installed. Then it would be a matter of resizing the Windows partition, creating an extra partition, copying over the data from the old to the new, and updating /etc/fstab.

---

### Post by technel on 2006-08-20
Good idea, thank you!

---

### Post by neouser99 on 2006-08-21
you can resize a ntfs partition. check this guy out first: 
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

then, to do the resizing, you must do this. you have to turn off the swap partition that windows uses if it is on the main ntfs drive, assuming that it is. then you have to defrag the entire partition, sometimes a few times. this is because windows places its swap file at the very end of the logical partition, making it very difficult for any partitioners to do any resizing. i have successfully accomplished this before, so i know it can be done. good luck.

I would also go with meng, whatever gigs you recover from the ntfs, turn them into the /home partition.

-neo

---

