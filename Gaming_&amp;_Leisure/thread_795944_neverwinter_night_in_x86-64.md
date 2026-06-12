---
title: "neverwinter night in x86-64?"
date: 2008-05-16
forum: Gaming &amp; Leisure
---

### Post by awec56a8 on 2008-05-16
hi, 
has anyone got nwn to work in x86-64 or in i386. if so can any kind folk provide the necessary step of how-to?

thank you for your kind help

regards,

awec56a8

---

### Post by Cappy on 2008-05-16
[http://gaming.gwos.org/doku.php/guides:64bit:nwn](http://gaming.gwos.org/doku.php/guides:64bit:nwn)

---

### Post by awec56a8 on 2008-05-18
hi cappy,
thank you for your tip, but it didn't work for my case, later i dig around the web i found out libSDL120 was causing the problem. since i am using hardy, the hardy version is newer than the one provided by nwn . the game just won't run at all. well the remedy is just delete the 2 files libSDL120 by nwn. now i can enjoy some orcs slaying.

regards,

awec56a8

---

### Post by Perfect Storm on 2008-05-19
Which is actually what you do by changing the line 10 to **export LD_LIBRARY_PATH=:./miles:$LD_LIBRARY_PATH ** (some of the last in the guide). It tells nwn not to use its own libSDL.

---

