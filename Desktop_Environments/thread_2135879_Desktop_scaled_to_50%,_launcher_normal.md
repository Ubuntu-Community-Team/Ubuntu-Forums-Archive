---
title: "Desktop scaled to 50%, launcher normal"
date: 2013-04-15
forum: Desktop Environments
---

### Post by bibach on 2013-04-15
I'm running a basically stock installation of Ubuntu 12.04 as a VM under VirtualBox 4.2.6 on an OS X 10.8 host system.  The VM is configured with two displays, appearing as two windows on the OS X screen.  Recently, I've had it happen several times that the entire desktop suddenly scales down to 50% of its proper size, centered in the display.  That is, the background and all of my windows scale, but the launcher and top panel (menus, indicators, etc.) still appear at their correct location and size.  The mouse cursor is also able to move around the display normally and the system registers movements and button clicks as if the desktop were not scaled (making mouse usage very tricky!).

This seems to occur when I use the Ctrl-Alt-T shortcut to start a new terminal window, but not every time.  I recently installed the Compiz Configuration Settings Manager (CCSM) application to tweak a few things (mostly a few keyboard shortcuts and snapping behavior when moving windows).  Setting up shortcuts for the Enhanced Zoom plugin (normally enabled but with no shortcuts configured) allows me to get the desktop back to approximately normal size, but with unfortunate panning behavior as I move the mouse, since the plugin thinks I'm zoomed in.

Any ideas on what might be causing this behavior and how to fix it either as it occurs, each time, or more permanently, so it won't happen any more?  Restarting Compiz (with the --replace option) from a terminal window does seem to fix the problem, but also shuffles around window positions, so I'd like to find a less disruptive fix.

Thanks!

-Brandon :)

---

