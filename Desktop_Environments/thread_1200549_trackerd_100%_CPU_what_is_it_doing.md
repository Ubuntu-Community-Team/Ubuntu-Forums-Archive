---
title: "trackerd 100% CPU: what is it doing?"
date: 2009-06-30
forum: Desktop Environments
---

### Post by mcarro on 2009-06-30
After a strange experience with beagle (it stopped indexing, and I saw no reason for that in logs, etc) I decided to try tracker.  So good so far, but now trackerd is using 100% of one of my laptop's two cores, and it is not accessing disk in a noticeable way.  It's been like this for quite some time now (some hours?).  I suppose that it can be optimizing indexes, making some bookkeeping, etc.  Could that be the case?  Or may it be just endelessly polling for something which is not arriving?  The tracker-related process in my laptop are currently:

mcarro    3154  0.0  0.2  19068  7112 pts/1    S+   12:39   0:00 tracker-applet
mcarro    4481 36.5  0.6  85012 20608 ?        RN   Jun29 434:47 /usr/lib/tracker/trackerd
mcarro    4482  0.3  0.1  29232  4908 ?        S    Jun29   3:53 tracker-applet
mcarro   30029  0.0  0.3  28472 11232 ?        SN   11:56   0:00 /usr/lib/tracker/tracker-indexer

in case this helps.

Thanks for any help!

---

