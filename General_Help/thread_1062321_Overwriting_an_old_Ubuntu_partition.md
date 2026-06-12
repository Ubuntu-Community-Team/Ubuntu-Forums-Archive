---
title: "Overwriting an old Ubuntu partition?"
date: 2009-02-06
forum: General Help
---

### Post by skrimpy on 2009-02-06
Needing to know if this is possible and how if so:

I upgraded my business computer from Feisty to Hardy when Feisty's support life ended.  I wanted to do a clean install of Hardy but kept my Feisty on a small 8GB partition in case I messed something up with the Hardy install, or had forgotten to back up something, etc.

Fast forward 3 months to now:  My Hardy changeover has been flawless.  I'd like to have my Hardy partition take expand over the 8G Feisty partition.

I used my Hardy LiveCD to wipe the 8g partition so it is now unallocated.  However, I see no option to expand my Hardy partition over that.

My husband says since the 8G partition is in front of my Hardy partition it may be impossible for me to expand the Hardy partition over it, but he's not positive.

Will it be possible for me to have Hardy's partition expand over the 8G partition?  If so, how?  If not, is there any way I can do anything useful with this partition or will I just have 8G sitting around until the next LTS comes around and I upgrade the business computer again :p ?

---

### Post by zvacet on 2009-02-06
Download [Gparted live CD]("http://gparted.sourceforge.net/") and with it you will be able to expand your Hardy partition to the unallocated space.

---

### Post by drs305 on 2009-02-06
Yes, you can expand it "left" with a couple of caveats. 

The two partitions will both have to be either primary or both logical partitions (inside the extended partition).  You can't expand a logical partition to take space from a primary partition. You would first have to expand the extended partition to take up the space. Once it is within the extended partition, you could do what you want.

Secondly, combining free space to the left of the partition requires that the entire contents of the existing partition be moved, so it will be a slow process. 

Also, because a lot of bits will be shuffled around, make sure you create backups of any important data - preferably not on the same drive (in case the partitions get really messed up).

Since you will be working with system partitions, they will need to be unmounted. Thus the need for the LiveCD, gparted CD or a SystemRescueCD, which all will let you run gparted with the system unmounted.

---

### Post by louieb on 2009-02-06
Maybe. GParted can grow a partition to the left. But be warned it going to take quit a bit of time. Can you post a screen-shot of Gparted. (press alt+prtScreen to capture just the Gparted window). 

Just a thought. Having a small partition available for testing before the next upgrade is a pretty good thing. Unless you in a crunch for space might be best to leave as is.:D

---

### Post by skrimpy on 2009-02-06
Thank you for your replies :)  I'm not really in a crunch for space, just thought it would be nice to have it all nicely put back into one partition.  I have the entire HDD for Ubuntu and my Hardy installation isn't even taking up 8G yet so there's lots of space.  I also made backups of everything before I even booted with the LiveCD :p  

Here is the requested screenshot:

---

### Post by skrimpy on 2009-02-10
The Gparted LiveCD worked perfectly, thank you!

---

