---
title: "Quake 4 transparancy fix without performance hit"
date: 2007-07-29
forum: Gaming &amp; Leisure
---

### Post by darundal on 2007-07-29
Ok, I am sure plenty of you out there (maybe) play Quake 4. Some people have an issue where some surfaces that are supposed to be transparent (usually windows) appear as opaque. The standard fix is to do one of two things. Either set r_multisamples to 0, or set r_multisamples and r_alphaToConverge to 1. However, the first solution did not work for me, and the second solution caused a major performance hit. So, I tried just making sure the the values for r_multisamples and r_alphaToConverge (which wasn't even in my config file before I tried the second solution) were at the same value (0) and everything worked. Apparently, that value isn't always added to the config file for some reason, so make sure that it is in there if your transparencies don't work.

---

### Post by mrtomservo on 2008-07-17
I know it's a bit late, but I can confirm that changing the r_alphaToConverge to 0 works for me too.  1.4.2 Q4, ATI binary, Heron.

Thanks for the info!!

---

### Post by Durandal512 on 2010-07-09
I know this is two years since the last post, but I just thought I'd say that you need to change the "alphaToCoverage" entry, NOT "alphaToConverge".

---

