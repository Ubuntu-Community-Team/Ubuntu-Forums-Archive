---
title: "Hard drive accessed every second, why?"
date: 2009-01-03
forum: General Help
---

### Post by cometa2k7 on 2009-01-03
I'm currently using 64-bit Intrepid, and I don't know why, but my hard drive is accessed every second.

I have the system monitor running on my panel, with the disk monitor visible, and every third pixel or so is marked as a write operation. Can someone please tell me why this is so? And can I prevent this, or limit it somewhat?

---

### Post by dnoyeb on 2009-01-03
are you using RAID?

---

### Post by sdennie on 2009-01-03
It's because of the ext3 journal commit time and the kernels dirty back writeback functionality.  If you don't like the disk being written this often, see [  HOWTO: Decrease disk activity]("http://ubuntuforums.org/showthread.php?t=839998")

---

### Post by cometa2k7 on 2009-01-04
> **dnoyeb said:**
> are you using RAID?

Not that I'm aware of, but to be honest, I don't really know.

---

### Post by cometa2k7 on 2009-01-04
That tutorial didn't work, the dirty writeback command were not found for some reason.

---

### Post by exploder on 2009-01-04
Is your hard drive LED flickering every few seconds? My machine does this flickering and there is nothing wrong. 

> That tutorial didn't work, the dirty writeback command were not found for some reason. 

Is your hard drive making a lot of noise?

Try turning off Tracker in "Sessions", this will reduce disk activity and Tracker doesn't really do anything anyway. I think that you are seeing the same thing I do on my machine and most likely everything is fine. My computer did this even when it had Vista installed and I think it is just the sensitivity of the hardware.

---

### Post by albinootje on 2009-01-04
> **cometa2k7 said:**
> I'm currently using 64-bit Intrepid, and I don't know why, but my hard drive is accessed every second.

I have the system monitor running on my panel, with the disk monitor visible, and every third pixel or so is marked as a write operation. Can someone please tell me why this is so? And can I prevent this, or limit it somewhat?

Fire up top in a terminal :
```

top

```
press "s", then press "1", then press "P" or "M".
Try also :
```

watch -n1 ps auxw

```

It could be an indexer for tracker, or the update manager, or perhaps an indexer for your music collection.

---

### Post by cometa2k7 on 2009-01-05
> **exploder said:**
> Is your hard drive LED flickering every few seconds? My machine does this flickering and there is nothing wrong. 



Is your hard drive making a lot of noise?

Try turning off Tracker in "Sessions", this will reduce disk activity and Tracker doesn't really do anything anyway. I think that you are seeing the same thing I do on my machine and most likely everything is fine. My computer did this even when it had Vista installed and I think it is just the sensitivity of the hardware.


I know that there is nothing wrong, it just irritating. The LED flashes, and I can hear the disk being accessed.

I turned all indexing off, and it doesn't change anything.

---

### Post by albinootje on 2009-01-05
> **cometa2k7 said:**
> I know that there is nothing wrong, it just irritating. The LED flashes, and I can hear the disk being accessed.

I turned all indexing off, and it doesn't change anything.

Linux uses background processes all the time, and with ext3 a journal is used.
Is your swap space already being used ?
```

free -m

```

(Interesting signature. I agree, and the same for Amiga, also far ahead at the time, as my Amiga friends showed me)

---

### Post by cometa2k7 on 2009-01-06
I'm currently using 33.6Mb of swap - I still have more than half of my RAM free (of 2Gb), so swap really isn't used much, if at all.

I think I may have set up ext3 Journaling, in fact, I'm pretty certain. Still, is there any way to make this happen with reduced frequency. I'm on a laptop, so power outage is no problem.

---

### Post by sdennie on 2009-01-06
The tutorial I posted above should work fine.  What specific errors are you getting?

---

