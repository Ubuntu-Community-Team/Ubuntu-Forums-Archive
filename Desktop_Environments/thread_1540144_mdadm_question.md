---
title: "mdadm question"
date: 2010-07-27
forum: Desktop Environments
---

### Post by ormeskirk on 2010-07-27
OK, this explanation could take a paragraph or two.  I have 7 hard drives in my system.  One is a 250GB PATA I use for the Ubuntu install, 3 are 1.5TB SATA Seagates and the other 3 are 1TB SATA Seagates.  I have had to replace 4 drives (one of them is the same drive twice) in order to get 6 that actually work well.  That's a 40% failure rate.  Most of the failed within a week or so of putting them in.  

Through all of that I have learned a few things and now have them configured as follows.  I have all six of them Raid5 with 1TB partitions.  And then the 3 extra 500GB partitions I put as Raid 5 also.  Seems weird, but it saves 1TB of space instead of having 3 1.5TB RAID5 and 3 1TB RAID5.

I then use LVM to make it all one big 6TB drive. Yummy, lots of space. :)

Here's the problem I have had the last couple of times I restart the computer the 6X1TB RAID does not start up, or I should say it has all the drives as spares (the 3X500GB RAID starts fine).  I have to use --force to get the raid to load, and all 6 load fine.  I believe it says something about having to write something to two of the drives (I believe it is something about the superblock) to make them the same.  I'm sorry I did not catch the message.

Is that enough information for someone to tell me why it does this?  It's done it twice now, when I reboot the computer.  As long as the computer stays running, they are perfectly happy.

Thanks.

---

### Post by ormeskirk on 2010-08-03
I have come to the conclusion that I think it is my power supply.  It is 8years old and I have to use PATA to SATA power adapters for all my drives.  

The problems started when i upgraded from 3 drives to 5 drives in my array.  I've ordered a new power supply.  I'll post if it solves the problem.

---

### Post by ormeskirk on 2011-03-05
The new power supply did solve the problem.

---

