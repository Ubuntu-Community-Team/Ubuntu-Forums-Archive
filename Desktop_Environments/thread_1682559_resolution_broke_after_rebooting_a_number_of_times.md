---
title: "resolution broke after rebooting a number of times without monitor"
date: 2011-02-06
forum: Desktop Environments
---

### Post by phazei on 2011-02-06
I've been trying to test out and get vino-server to work without being logged in.  In that process I've been switching back and forth between two computers with a KVM switch and have been rebooting without the monitor on ubuntu a number of times and connecting with VNC.

Somehow during that process, the resolution broke.  It no longer detects the monitor properly when it had been before I started.  Max res of monitor is 1650x1080 but it's only doing 1300xSomething.

I tried 'sudo dpkg-reconfigure xserver-xorg' but that seems to be depreciated.  I didn't even have a Xorg.conf file in the X11 dir.  I tried Xorg -configure and copied over the new one with no results.

I can't get the resolution to fix itself.  I have no special video card, just whatever is on board, there were no proprietary drivers for it.

---

