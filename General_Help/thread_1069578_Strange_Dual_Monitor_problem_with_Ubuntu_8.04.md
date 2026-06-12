---
title: "Strange Dual Monitor problem with Ubuntu 8.04"
date: 2009-02-14
forum: General Help
---

### Post by Zhengtonic on 2009-02-14
I have a dual monitor setup (Siemens P19 on DVI and a miro 19'' on vga) running ubuntu 8.04. After a update (i did not watch what was updated)
my Siemens P19 always shuts down after 30 seconds. If i restart the monitor
it stays on for another 30 seconds, but will eventually go off again.
The strange thing is ... the monitor does not say that it has lost the signal. It just stays black. Anyone know what this might be? 

btw. i use the restricted nvidia drivers.


best regards,

zhengtonic

---

### Post by Dal1980 on 2009-02-14
I am in no way an ubuntu expert (infact I've just started with all this the last week or so) but have you set the nvidia properties to TwinView and checked if making one primary has changed anything?

Cheers
Dal1980

---

### Post by khelben1979 on 2009-02-14
If you have a screensaver which shuts your monitor off after 30 seconds, you might be interested in adjusting these settings. The top command will reveal what processes you have running over there

Other than that: try reinstalling the nVidia drivers, they probably broke together with an update.

Some updates upgrades the kernel and in the process when this occurs some things which worked before can brake.

---

