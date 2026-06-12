---
title: "Frequent plasma 5 crashes in Kubuntu 15.04"
date: 2015-05-26
forum: Desktop Environments
---

### Post by pwabrahams on 2015-05-26
I'm running Kubuntu 15.04 and I get frequent Plasma 5 crashes -- several in an hour, mostly while running Firefox.  They don't seem to be hurting me, though -- I can just ignore or dismiss the warning and continue doing whatever I was doing.  When I've tried to report the bug, I get the message that there isn't enough information.   Is this a common experience?  What should I do about it?

---

### Post by alikazmi-2040 on 2015-05-26
[SIZE=2]1- Try installing kdelibs5-dbg first of all. That will (hopefully) add the required debug symbols to generate a meaningful crash report.

2- Try creating a new user and see if the crashes persist for the new user as well as it could be a configuration issue.

3- Do you have desktop effects enabled? If you do, does turning them off have any effect?

4- Did you do a fresh install or update from 14.04 or 14.10?
[/SIZE]

---

