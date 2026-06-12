---
title: "Is Beagle-demon eating my memory?"
date: 2005-10-14
forum: Desktop Environments
---

### Post by kwisatz on 2005-10-14
This is my top output:
10598 kwisatz   16   0  256m 115m 7468 S  0.0 24.5   1:10.84 mono
 7417 root      15   0  161m  18m 8544 S  3.3  3.8   1:29.33 Xorg
 9374 kwisatz   15   0  123m  41m  19m S  0.3  8.7   1:09.62 firefox-bin
13080 kwisatz   16   0 74108  51m  10m S  0.0 10.9   0:03.08 evince

Beagle has the size of 256 Mb! My laptop with 512 Mb of RAM is swapping like a crazy! 
Is it normal?

Thank you,

---

### Post by BenjyD on 2005-10-14
Beagle is probably still indexing your hard drive contents ready for searching - it takes a while the first time you start it up. The memory usage should drop off once it's finished. Although, it is a Mono app, so it's always going to consume a fair bit of memory.

---

### Post by kwisatz on 2005-10-14
Are you sure? This isn't the first time I use beagles and I suppose that my directories are already indexed...and then my CPU is not working! 
He is silently eating my memory...now I shutted down him because my swap was too high (70%)...

---

### Post by BenjyD on 2005-10-14
I had seen that behaviour from an older version of Beagle (which was why I stopped using it :-) ). I've just started the current Breezy version of Beagle running and it's taking ~20Mb of RAM doing the initial indexing, so I guess what you're seeing isn't normal.

It sounds like you've hit a bug - IIRC, I had problems with versions of Beagle getting stuck in some kind of infinite loop with some directories.

---

