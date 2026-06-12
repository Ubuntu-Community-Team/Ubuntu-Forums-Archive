---
title: "Beryl without Xgl: something for nothing?"
date: 2007-01-03
forum: Desktop Environments
---

### Post by disbelief0 on 2007-01-03
OK, so I've got this nifty old Toshiba laptop with integrated ATI video (32 MB shared memory -- ugh) with something like 400 MB system RAM (long story). I'm running Ubuntu 6.10 Edgy.

I installed Xgl on it with Beryl as the window manager (and its Emerald window decorator). I was doing fine, though the system was a bit slower. I noticed in System Monitor that Xgl was using (at the time) something like 86 MB of memory. (On a fresh boot it uses closer to 44 MB.) So I logged out and switched to a Gnome session, though Beryl was still set up as the window manager. I thought, fine, I'll just switch back to Metacity and be rolling. But before I did that, I noticed I still had all the Xgl features -- wobbly windows, rotating cube, scaling, zoom, etc.

I check my System Monitor again and Xgl is NOT running (which is good -- it shouldn't be). Why do all the features still work? Beryl isn't using any more memory than before, and no running process is using nearly as much memory as Xgl would've been. Did I get something for nothing? Are resources being used, but hiding from me?

I have the same setup on my desktop, but I'm not at home to try that there.

How can this be?

---

### Post by mercurysquad on 2007-01-03
Beryl can use either Xgl or AIGLX. Ubuntu 6.10 comes with new xorg7.1 which has AIGLX built-in and enabled by default, so there really is nothing you need to do to get beryl working (ie. no need to have Xgl running).

Beryl auto-detects whether it is running on aiglx or xgl, so when you closed down xgl, beryl switched to aiglx. That's my understanding.

Actually on old systems, it is suggested to use aiglx because it is faster. So if you are having problems, just get rid of Xgl totally.

---

### Post by darrenm on 2007-01-03
Yup, a nice feature of Edgy :)

---

