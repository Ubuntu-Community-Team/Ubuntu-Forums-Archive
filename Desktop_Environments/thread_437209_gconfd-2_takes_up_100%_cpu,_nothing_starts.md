---
title: "gconfd-2 takes up 100% cpu, nothing starts"
date: 2007-05-08
forum: Desktop Environments
---

### Post by romulusnr on 2007-05-08
Whenever I log into my gnome session, Gnome starts up my startup applications, and then gconfd-2 takes up 100% CPU for the next 6 minutes. During this time nothing started from within the session will be loaded, but stay in limbo until such time as gconfd-2 drops its high load -- then suddenly everything you tried to load over that time will appear. During the time gconfd is at 100% there is no disk use.

Why is gconfd effectively locking up my session upon login?

---

