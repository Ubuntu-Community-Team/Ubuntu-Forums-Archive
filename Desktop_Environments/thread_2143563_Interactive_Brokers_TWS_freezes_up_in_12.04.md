---
title: "Interactive Brokers TWS freezes up in 12.04"
date: 2013-05-09
forum: Desktop Environments
---

### Post by kodb on 2013-05-09
I've been using IB for my personal stuff a while and have switched over our IRAs.  I'm now having some difficulty with getting the TWS which is java based to run.  It keeps freezing up and when I take a look at the system monitor it seems to be pegging cpu at 156% or so. I checked below:
```

bob@MD1-U:~$ java -version
java version "1.7.0_21"
Java(TM) SE Runtime Environment (build 1.7.0_21-b11)
Java HotSpot(TM) Server VM (build 23.21-b01, mixed mode)

```
So it appears I'm running the latest oracle version of java.  I had similar problems with openjdk so I purged that and installed the oracle version.
Anyone else have any experience with this platform or hints?
Thanks
Bob

---

