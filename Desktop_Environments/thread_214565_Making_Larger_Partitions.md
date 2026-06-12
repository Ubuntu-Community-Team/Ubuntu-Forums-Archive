---
title: "Making Larger Partitions"
date: 2006-07-12
forum: Desktop Environments
---

### Post by jrjr on 2006-07-12
My system has an 80 gig SATA drive. Currently first partition (C)is 15 gigs and holds XP install. Second part is program files, etc. C is nearly full. Can I use the partition utility in Ubuntu to adjust my C drive and make it a bit larger before making my dual boot part at the end of D? 

I read lots about making things smaller but not larger. Of course back up is necessary but what are my chances of success?

---

### Post by Scunizi on 2006-07-13
What was reccommended to me was gparted to increase my "/" partition.  I haven't tried it yet but that's the consensus.

---

### Post by krazykirk on 2006-07-13
Yeah Gparted is the way to go!

I think the best way to do that is to get the Gparted Live Cd (Only 20mb) and burn that onto a blank cd, and then boot off it! That way you can resize your  drives to whatever you want, so you can shrink a drive and make the other one bigger :)

---

### Post by jrjr on 2006-07-13
Ok thanks, Im sure there is a link around here somewhere for that. Will check it out. :mrgreen:

---

### Post by Herman on 2006-07-13
Here's a link: [GParted LiveCD]("http://gparted.sourceforge.net/")

---

### Post by Scunizi on 2006-07-17
Well I tried Gparted and managed to hose thing up enough that I had to do a full reinstall (which is problematic enough with 2 sata drives and 1 ide).  Gparted also managed to do something with one partition I tried to make larger but is now unaccessable.

---

