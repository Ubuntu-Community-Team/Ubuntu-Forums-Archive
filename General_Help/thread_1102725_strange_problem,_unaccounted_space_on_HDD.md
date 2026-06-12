---
title: "strange problem, unaccounted space on HDD"
date: 2009-03-21
forum: General Help
---

### Post by v1nsai on 2009-03-21
Space is getting a little tight on my hdd, so I'm running disk usage analyzer and it's giving me some weird numbers.  My ubuntu partition is 74 gigs of the total 120 gigs available on this drive, and the dua reports that only 54 gigs are used, but when I right click my filesystem and look at properties, it reports that only 3 gigs are free.  Near the top of the dua window, it lists my total filesystem capacity as 139 gigs, and that 15 are free.

Another strange problem involving disk space has been my flash drives.  3 of my 2 gig flashdrives are completely empty, yet only report that around 500 megs are free, but won't let me put anything on them because they are full.  Another one works just fine :confused:

I'm just confused right now...anyone know what's goin on?

---

### Post by dcstar on 2009-03-21
> **v1nsai said:**
> Space is getting a little tight on my hdd, so I'm running disk usage analyzer and it's giving me some weird numbers.  My ubuntu partition is 74 gigs of the total 120 gigs available on this drive, and the dua reports that only 54 gigs are used, but when I right click my filesystem and look at properties, it reports that only 3 gigs are free.  Near the top of the dua window, it lists my total filesystem capacity as 139 gigs, and that 15 are free.
.......
I'm just confused right now...anyone know what's goin on?

Do a forum search on "gksudo baobab"

---

### Post by v1nsai on 2009-03-22
Oh, nice tool thanks for that.  That explained my filesystem but I'm still not getting all my space on my flash drives.  One of them is showing 1.4 gigs but on a 2 gig drive thats still not very good, and the other two are still showing only 300-ish MB free, and they're completely empty.  I looked around in 'gksudo nautilus' and tried to view hidden files, but still empty, what else could be going on?

---

### Post by drs305 on 2009-03-22
Are you familiar with root Trash and the possibility you have hidden trash files residing on you system? They take up space until the bin is emptied. If it is trash deleted by root, this trash bin isn't emptied in the normal manner.

Check out the guide in my signature line regarding Trash. It also gives some other things to try to discover what may be taking up space on your partition, such as backups which are incorrectly saved to the system partition instead of a removable drive.

Also, about 5% of your space is reserved for use by the system.

---

### Post by v1nsai on 2009-03-22
Nice post, lots of good info there, I didn't see anything that led to any answers about the flash drives, so I went with plan B and formatted with GParted.  I'm a little curious about what caused the problem and I'd be interested in any answers about how to fix the problem instead of nuking the whole thing, but hey at least I got my flash drives back.

---

