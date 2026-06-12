---
title: "Slow write speeds to mdadm RAID 5"
date: 2006-10-03
forum: Desktop Environments
---

### Post by windycitywonk on 2006-10-03
Newb here.  I'm running Ubuntu 6.06 with 3 disks in RAID5 via mdadm.  On my Gb LAN, I get read speeds (copying files from the RAID storage to Windows XP) of 30MB/s, but my write speeds are terrible, coming in at less than 1MB/s.  Any suggestions?

---

### Post by Ocxic on 2006-10-03
raid 5 is farily slow, as it causes too many simulatious writes to one drive. read here for an explination:
[http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks#RAID_5](http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks#RAID_5)

and I would choose either raid0, raid1, or raid0+1
or
logical volume managment (LVM)

---

### Post by windycitywonk on 2006-10-03
> **Ocxic said:**
> raid 5 is farily slow, as it causes too many simulatious writes to one drive. read here for an explination:
[http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks#RAID_5](http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks#RAID_5)

and I would choose either raid0, raid1, or raid0+1
or
logical volume managment (LVM)

Thanks for reply.  Is there any way of tweaking the software RAID 5 to produce better write speeds?

---

### Post by xXx 0wn3d xXx on 2006-10-03
> **windycitywonk said:**
> Thanks for reply.  Is there any way of tweaking the software RAID 5 to produce better write speeds?

what is the output of 

> sudo hdparm /dev/hda

do you have dma enabled ?

---

### Post by windycitywonk on 2006-10-03
I'll check that out when I get home from work tonight.

---

### Post by windycitywonk on 2006-10-03
> **xXx 0wn3d xXx said:**
> what is the output of 



do you have dma enabled ?

The output shows that all of my drives have DMA enabled.

---

