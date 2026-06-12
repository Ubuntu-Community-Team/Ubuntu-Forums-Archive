---
title: "Intel HD Graphics Problem. CompizConfig"
date: 2014-09-03
forum: Desktop Environments
---

### Post by hai3 on 2014-09-03
After Install Ubuntu 13.04 through wubi, everything ran fine, but i started getting graphic problem after used CompizConfig.
I checked desktop cube, Cube Rotate and my system run little laggy, but fine. Then I checked 3d WINDOWS and i got a graphic problem, i wasted 2 hour on google but didnt solve problem.

i am just a 13 years old vietnamese, and new to linux. I only know a little basic programming. I can't fix anything

Specs:
Intel Core i3 3240 3.4 ghz 
ram: 3.8 GB
Intel HD Graphics 1000
OS: Windows 7/ Ubuntu 13.04

---

### Post by deadflowr on 2014-09-04
Unfortunately, 3d windows is broken.
Has been since as least Ubuntu 12.10.
I don't see a fix for it in the near future either.
I think there is bug report (or two, or three or ten) on it.

Cube will still work, without the 3d window effect, though.

Edit: To add also, 13.04 has reached end of support life, so it would be wise to upgrade to a supported release.
Unfortunately, I have no idea how a wubi upgrade works...

---

### Post by QIII on 2014-09-04
Not "broken" exactly.  No longer available.

Last I heard Compiz was down to three developers. Around 2010, Sam Spilsbury made a desperate call for people to help continue development of some of the features, but not much help was forthcoming.

Choices had to be made and 3d windows was cut.

kwin still has that feature in KDE.

---

### Post by deadflowr on 2014-09-04
> **QIII said:**
> Not "broken" exactly.  No longer available.

Last I heard Compiz was down to three developers. Around 2010, Sam Spilsbury made a desperate call for people to help continue development of some of the features, but not much help was forthcoming.

Choices had to be made and 3d windows was cut.

kwin still has that feature in KDE.


I think you mean no longer under development.
It's still available up to, at least, 14.04.

---

### Post by QIII on 2014-09-04
That would suggest that it was actually *brought back, *which is nice.  It definitely was not available for quite a while.

Sam blogged about it being cut.  After he left Canonical in 2010 someone must have taken it on.

Well, cool then.

---

### Post by buzzingrobot on 2014-09-04
Isn't it the case that since Unity is currently implemented as a Compiz plugin,  Canonical maintains it in order to keep Unity going, but isn't likely to devote many resources to maintaining parts of Compiz -- like wobbly windows and such -- that it doesn't use?  (Post-Mir, doesn't Compiz go away?)

I can get workspace changing via wheel scroll working with CCSM on Unity, but other tweaks very often break something, so I just don't go there.

---

