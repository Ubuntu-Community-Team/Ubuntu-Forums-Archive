---
title: "X Window problem?"
date: 2006-03-09
forum: Desktop Environments
---

### Post by hajk on 2006-03-09
I have some problems with RealPlayer and MPlayer that are possibly related to X Windows. 

Once a real audio or video stream is underway in RealPlayer, then the RealPlayer window and its buttons/submenus become rather unresponsive, taking up to 30 seconds to react. Also, the video is choppy, halting every few seconds or so. I've tried several versions of RealPlayer 10: from the Marillat repository, an rpm-package from DNA Helix installed via alien, a recent version from CVS..., all show the same problem.

The same real video plays smoothly in MPlayerplug-in, and also real audio streams play well in MPlayer. But here, too, moving the MPlayer "control panel" across the screen is rather jerky.

My computer has lots of RAM and CPU power, the graphic card is GeForce 6200 with 128MB, the driver is nvidia (the same happens with the nv driver). No other problems with X: Totem-xine plays DVDs beautifully. 

Does anyone recognize these symptoms? Any idea about a solution?

---

### Post by RAOF on 2006-03-09
The only thing I can think of you might want to check is what video output mode Realplayer & Mplayer are using - they can have a **big** impact on performance.

---

### Post by hajk on 2006-03-09
Yes, I've already played with various video and audio settings -- no change. I've also compared settings with those on a couple of other computers that run Breezy. There  the only difference that I notice when wading through /var/log/Xorg.0.log (or gdm/:0.log) is the following message (2x):

Symbol __glXgetActiveScreen from module /usr/X11R6/modules/extensions/libdri.a is unresolved!

Don't know whether this means anything, it appears both with the "dri" module loaded and not loaded. May be an X wizard would know...

---

