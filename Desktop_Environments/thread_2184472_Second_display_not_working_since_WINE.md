---
title: "Second display not working since WINE"
date: 2013-10-29
forum: Desktop Environments
---

### Post by hakamade on 2013-10-29
I tried an old game with Wine, and it had a problematic side effect: my second display is no longer working. When I go to System Settings -> Displays, the second display is shown in light grey in the top right corner. It can be dragged around, but otherwise doesn't react to anything. Clicking Default Settings has no effect, and Previous Settings is disabled.

xrandr lists the display, but xrandr -d [output name] --auto causes error "Can't open display HDMI-0". Anything else I tried with xrandr has no effect. During startup, image is shown on both displays until KDE desktop is ready, then the secondary display goes to "No signal".

I've got a two-day old Kubuntu 13.10 installation with little additions to it.

---

### Post by hakamade on 2013-10-30
So after a few boots and a night off, today the second display has become responsive in display settings. Put it back to use and everything's fine. Go figure.

---

