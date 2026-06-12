---
title: "&lt;1420n&gt; mplayer -vo xv (intel video chipset)"
date: 2007-09-01
forum: Dell  Ubuntu Support
---

### Post by syssyphus on 2007-09-01
has anyone gotten it to work? I am using gl now because xv results in no video, and x11 of course requires -zoom, gl2 completley messes up the display, any ideas?

---

### Post by colo on 2007-09-02
What IGP have you got? G965/X3000 or newer?

---

### Post by syssyphus on 2007-09-02
> **colo said:**
> What IGP have you got? G965/X3000 or newer?

GMA X3100 (the mobile version of the GMA X3000 used in the Mobile 965GM chipset.)

---

### Post by colo on 2007-09-03
GMA X3000 and above do not have any video overlay silicon any more. `gl`, however, works fine as the intended replacement. `gl2` does so, too, since version 2.1.0 of the xorg-video-intel driverfor me.

---

### Post by kuja on 2007-09-03
xv works fine in Gutsy :)

---

