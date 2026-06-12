---
title: "dbus-daemon spawning lots of processes."
date: 2005-01-13
forum: Desktop Environments
---

### Post by astoltz on 2005-01-13
Greetings all,

After normal use of my computer for a couple days there are many processes listed for dbus-daemon-1 (I think the belongs to the Hardware Abstraction Layer).  Today, a ps -A command showed 16 different processes.  I've not done much troubleshooting but I think every time I log-out / log-in, another dbus-daemon process is started and the old one stays around for good measure.  My remedy has been to stop HAL, killall bus-daemon-1, then restart HAL.  Through all of this, the system seems to work just fine.  This can't be normal - anybody have any ideas?  

It's a pretty stock Warty install on an AMD Sempron.

Thanks for looking.
   -Al

---

