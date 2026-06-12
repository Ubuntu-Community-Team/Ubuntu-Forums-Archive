---
title: "Compiz not loaded on startup"
date: 2009-09-21
forum: Desktop Environments
---

### Post by edwinw on 2009-09-21
I'm having a problem with compiz not being loaded on startup.  I am running Ubuntu 9.04 and I installed the proprietary Nvidia driver using envyng, and compiz pretty well once it's started.  I added the following additional entries to System > Preferences > Startup Applications > Startup Programs:

compiz --replace --indirect-rendering --loose-binding
emerald --replace
fusion-icon --no-start (I also tried it without the --no-start option)

Fusion icon comes up by itself when logging into the desktop, so no problem there.  However, it appears that compiz and emerald aren't loading, I have to reload the window manager and everything works.  Just wondering how I can fix this, can anybody suggest any diagnostics to find out what's wrong?  Thanks.

By the way if it matters - I have a dual monitor setup running TwinView, but even with it off I still the compiz not starting problem.

---

