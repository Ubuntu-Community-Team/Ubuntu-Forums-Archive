---
title: "Hibernate fails, suspend works"
date: 2009-04-29
forum: General Help
---

### Post by mogliii on 2009-04-29
Ubuntu 9.04 32bit, full patched, 2.6.28-11-generic on IBM T40.

I had the beta of 9.04 installed and suspend/hibernate worked out of box. Now packages got updated (after final release) and strangely I can not hibernate anymore.

The screen turns black, the sleep LED blinks for a while, but then the screen shows up, prints 3 lines for a short time (can't recognize what it says) and brings me back to a dialog asking for me to unlock the screen.

I have pasted my dmesg output here:
[http://paste.ubuntu.com/160956/]("http://paste.ubuntu.com/160956/")

/var/log/pm-suspend.log just says "success" everywhere. No problem.

I think the problem is at line 35 of my dmesg. But what is device 0000:00:00.0?

I would be happy to have this working again.

---

