---
title: "Co-existence of xrandr, xscreensaver and pm-utils"
date: 2013-03-10
forum: Desktop Environments
---

### Post by JoeHallenbeck on 2013-03-10
Hello all,

is there anyone who really knows their xfce?

Some very erratic behaviour occurs when you connect a display through DisplayPort and then let your xcreensaver apply power saving by turning off all monitors after being idle for a while. Sometimes, after coming back to the PC, that particular display doesn't get any input signal. Re-running xrandr with the original display settings doesn't help. What actually (sometimes) does help:

1) switching ttys (via ctrl+alt+f#)
2) turning the graphical output off an on (e.g. xflock)
3) suspending and resuming the machine (and rebooting of course)

- quite unlucky it's often an unknown precise combination of the above.

Seems familiar to anyone? What's the cause of and solution to this problem?

Cheers

---

### Post by JoeHallenbeck on 2013-03-12
Really no hope?

---

