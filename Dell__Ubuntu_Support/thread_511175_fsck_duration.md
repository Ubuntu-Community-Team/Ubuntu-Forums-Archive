---
title: "fsck duration"
date: 2007-07-27
forum: Dell  Ubuntu Support
---

### Post by DonA on 2007-07-27
I hit the magic number of 28 reboots on my E1505n, so fsck was invoked on the big Dell Ubuntu partition.  Here's the message from /var/logs/checkroot:

> 
Log of fsck -C -a -t ext3 /dev/sda6 
Fri Jul 27 10:29:31 2007

fsck 1.40-WIP (14-Nov-2006)
os_part has been mounted 28 times without being checked, check forced.
os_part: 218185/14033920 files (6.8% non-contiguous), 27060957/112270220 blocks

Fri Jul 27 10:50:41 2007
----------------


Note the 21 minutes elapsed time.  I'm wondering if that's a typical and appropriate fsck duration, given the size of the partition.  As I was working from home and on a conference call (using twinkle) when the system froze (the cause of which I'm investigating), those 21 minutes seemed like an aeon.  But it may be normal.  (My other Ubuntu systems don't have such large partitions, so it's never taken sooo long.)

Any thoughts?  Thanks.

..DonA

---

### Post by jordon on 2007-07-27
The main partition on my E1505N is 105 GB, and it takes about 15 minutes to do a fsck. To give myself more control, I set the "magic number" to 50 boots and installed [Bonager](http://ubuntuforums.org/showthread.php?t=295262) so I can control when fsck will run next.

---

### Post by DonA on 2007-07-27
Thanks, Jordan.  I've installed bonager.  At least I won't be surprised by the next fsck.   ..DonA

---

### Post by Vogateer on 2007-09-01
My own Inspiron 1420n seems to be taking ages to do the fsck as well. As of right now the progress bar is stuck at 13%, and it never seems like my other systems take this long, and they're larger hard drives with larger partitions.

---

