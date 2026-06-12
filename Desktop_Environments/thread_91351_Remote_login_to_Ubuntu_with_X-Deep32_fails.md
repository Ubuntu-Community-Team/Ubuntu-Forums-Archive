---
title: "Remote login to Ubuntu with X-Deep32 fails"
date: 2005-11-17
forum: Desktop Environments
---

### Post by Morrigu on 2005-11-17
I've used Ubuntu with remote X from my windows machine using X-Deep32 by Pexus. This used to work fine, I used XDMCP+GDM.

I'm not sure if this happened when I upgraded to 5.10, but now X-Deep32 fails to start. I get the following error in X-Deep32 logfile:
```

DEBUGTRACE:[2348:xwin32pix.c:#328]:Thu Nov 17 07:39:18 2005
		xwin32CreatePixmap : Null hBitmap, Try with Low System Resource Mode Enabled
FATALERROR[2348]: Thu Nov 17 07:39:18 2005
		cound not create root tile######## X-Deep/32 X-Server Started on : Thu Nov 17 07:47:50 2005

```

I have tried with Low System Resource Mode, but it didn't help. I know X-Deep is old and support is hard to find, but it's the only free usable X-client (no, I don't consider Cygwin/X to be usable ;) I have been able to find.

Did something happen to GDM in 5.04 -> 5.10 update? How would I replace GDM with XDM or KDM?

I'm still able to connect with XThinPro, but it's commercial software and only runs for 15 or 30 minutes :( So the remote login and X seems to work, the problem is somehow with X-Deep32.

---

### Post by gjern on 2005-12-21
Hi
I get the same fault after changing from 5.04 to 5.10
It worked OK on 5.04 but after a clean installation of 5.10 it dont work anymore.
Have tried with x-deep and Cygwin/x and both do not connect.
Looks like the x-deep / Cygwin very shortly draws the UI-box for User / password and then resets leaving the screen blank.

---

