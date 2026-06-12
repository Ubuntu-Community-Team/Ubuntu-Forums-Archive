---
title: "Strange Desktop Resize Bug"
date: 2010-07-12
forum: Desktop Environments
---

### Post by MatthewPlanchard on 2010-07-12
Hey Everyone,

I've run into a weird little bug, which has persisted through the past few versions of the Linux kernel (currently running 2.6.32-24), so I figured I'd try to find out what is causing it.

If I leave my computer alone for a while, the screen will go black, and occasionally (not always) on resuming my session, the desktop has been resized to be significantly larger horizontally.  However, I'm pretty sure only the virtual desktop is being resized, as what is being displayed on the monitor remains exactly the same.

Panel function remains normal even with a resized desktop, but sometimes a new window will open in the extended area, and to access it I have to drag my mouse over into the beyond screen area and try to capture the window.  The desktops on the switch-desktop panel applet do appear to be extended horizontally as well when this happens, and Cairo-dock moves itself into the center of the new desktop, which is toward the right side of the visible screen.

Any ideas as to what might be going on here, or what program might be causing it?  I couldn't find a bug in Launchpad or any posts on here detailing this phenomenon.

Thanks.

---

