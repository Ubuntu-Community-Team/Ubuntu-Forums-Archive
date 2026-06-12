---
title: "[SOLVED] gdm seems to lock up and hibernate no longer works"
date: 2007-08-27
forum: Desktop Environments
---

### Post by rrwo on 2007-08-27
GDM no longer works. When I boot my laptop, the screen goes black with a circular mouse pointer that keeps spinning. It seems to have locked up.

I removed gdm (apt-get remove gdm) and that fixed it, sort of. My system boots up in the command line, but when I startx, my window/desktop manager (Xfce) seems to work fine, except that the system no longer hibernates when I close my laptop.  I've checked and my system power settings are unchanged.

Reinstalling GDM did not fix things.

I installed XDM, and that works as a login screen, but I'd like to know what's gone wrong. I'd also like to restore the ability of my laptop to hibernate (even selecting the option on logout does nothing).

I've not installed anything recently, but thought it might be because I started using vmware-player. But uninstalling vmware did not fix the problem.

Any advice on how to fix this or diagnose the problem?

[Update: I reinstalled Ubuntu from scratch to fix the problem. I've since upgraded to Gutsy, and this is not a problem as well.]

---

### Post by rrwo on 2007-08-29
Also, when it starts, I get messages complaining that there's no hibernation image (makes sense since hibernate isn't working, but I don't know if it should be expecting one or not).

And a message that avahi-daemon is stopped. I'm able to restart it with no errors, so I'm unsure why it's stopping it on startup.

---

### Post by rrwo on 2008-04-01
This was fixed by reinstalling Ubuntu. Not the best option, but the only one I could figure out at the time. I'm marking this as "solved" even though technically it wasn't.

---

