---
title: "desktop couch won't start"
date: 2010-11-19
forum: Desktop Environments
---

### Post by rcrath on 2010-11-19
Hi, 

I think I messed up some permissions needed to run desktop couch.   i follwed the instructions [here]("http://www.freedesktop.org/wiki/Specifications/desktopcouch/Documentation/Troubleshooting") for restarting, but did not read them carefully, and when the processes were not found, I ran the kill commands as root.  Since then, desktop couch will not start.  I tried a full purge/reinstall, but still no luck.  I filed a bug report [here]("https://bugs.launchpad.net/desktopcouch/+bug/674396"), but I don't think anyone has read it yet.  I am guessing running things as root reset some permissions somewhere, but I don't know where.  Any ideas?  If you need more details about exactly what I did, they are in the [bug report]("https://bugs.launchpad.net/desktopcouch/+bug/674396").  I'd appreciate any help.

---

### Post by rcrath on 2010-11-22
bump...

---

### Post by rcrath on 2010-11-28
Anyone?

---

### Post by nickbuntu on 2011-10-15
I just had and fixed this problem - thought I'd reply even though it's an old thread as someone might Google their way here as I did.

Had exactly the same problem, but running  /usr/lib/desktopcouch/desktopcouch-service directly will actually show you the error that's preventing it from starting. In my case some log files had been created by root. Deleted these and it all started working.

---

