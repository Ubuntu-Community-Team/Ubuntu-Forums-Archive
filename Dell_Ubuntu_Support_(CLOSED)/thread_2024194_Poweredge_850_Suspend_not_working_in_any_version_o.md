---
title: "Poweredge 850: Suspend not working in any version of ubuntu"
date: 2012-07-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by buges on 2012-07-13
I've just picked up a cheap dell poweredge 850 to replace my old athlon xp machine as a file sever in my house.

Suspend does not work at all! I've tried 10.10,11.04 and 12.04 all with the same results.

When i click suspend the screen just go's blank (it does not turn off the video card) if i move the mouse i get the unlock screen, running "sudo pm-suspend" from terminal does nothing at all. Also running "/sys/power# echo -n "standby" > state" gives me the error: "bash: echo: write error: No such device"


My old custom built machine running 10.4 suspended perfectly!

Any help would be appreciated.

Thanks

---

