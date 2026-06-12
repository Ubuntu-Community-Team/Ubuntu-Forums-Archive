---
title: "Single core games vs multi core CPUs power management ?"
date: 2009-05-21
forum: Gaming &amp; Leisure
---

### Post by Devport on 2009-05-21
Some of the games I play are old single core FPS ( e.g. RTCW : Enemy Territory and Warsow ). Those games fully use a single core at its full power but the other core ( in my case a 2Ghz dual core Athlon cpu ) will be clocked at maximum as well. Since I will be upgrading to an Intel Core 2 Quad soon I wonder if those games will make all ( 4 ) cores run at full power or is the Intel Core 2 Quad ( e.g. Q9300 ) power management advanced enough so that only one core will be clocked at full power but not the other 3 cores ?

If this is not the case what can be done to not waste a lot of power by having 4 cores running at full power while only one core is needed ?

---

### Post by Sigurd Suhm on 2009-05-21
Being a hobby game developer I hope I can provide a bit of input on this.

Basically how well the seperate cores of a processor is used during a game depends on how well the game is coded for multi core processor architectures. Old games will not be using multithreading at all and thus won't run any better on a 2.0 gHz Quad Core than on a 2.0 gHz Single Core. (This may be a bit simplified as the computer still has some threaded background processes from the OS and such.)

As for performance I'm not really sure that you can do a lot when working with several cores. As for the power management (which seems like the core (no pun intended) of your question) I'm probably not the right person to ask. I'm not really familiar with Intels Quad Core architechtures yet. However it would seem strange to me if it was impossible to find any software utilities that are able to work with the clock speeds of multiple cores in such architechtures. I'll have to pass this question on to another forum user more experienced in working with such hardware.

Hope I provided at least a bit of helpful info
Regards
Sigurd Suhm

---

