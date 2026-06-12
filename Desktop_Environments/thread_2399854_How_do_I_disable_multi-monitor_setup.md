---
title: "How do I disable multi-monitor setup"
date: 2018-08-30
forum: Desktop Environments
---

### Post by marcwetzel on 2018-08-30
Hi,

I use ubuntu on one hand as my desktop os, where the multi-monitor setup as it is, is quite useful (combining several displays to one big desktop), but on the other Hand I also use it for my embedded Systems.

For that I need to disable that feature completely, so that each display is adressed as one display, selectable by DISPLAY=0.1 (0.2, 0.3) as in the old times.
What do I have to do (de-install / configure / ...) to achive this?

2nd Question: How do I get the config file back, which normally is somewhere in /etc/X11/config or XF86config, or am I just looking in the wrong places?


BR
Marc
(using Ubuntu 18.04 lts desktop version)

---

### Post by TheFu on 2018-08-30
**lxrandr** is the easy way.  Uncheck the monitor you don't want enabled. I don't have 18.04, but guess that tool will still work.

---

