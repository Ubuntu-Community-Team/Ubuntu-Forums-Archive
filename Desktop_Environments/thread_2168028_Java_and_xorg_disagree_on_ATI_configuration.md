---
title: "Java and xorg disagree on ATI configuration"
date: 2013-08-16
forum: Desktop Environments
---

### Post by chris41 on 2013-08-16
Morning all, 

I'm experiencing a strange problem with a specialist setup I have.  I have a display wall of 18 monitors, connected to three ATI 6800 Eyefinity 6 cards (installed on a single PC running Ubuntu 12.04). I have the propriety ATI drivers installed, and I'm running three desktops, each containing six monitors that share one graphics card (Xinerama is disabled).   Using the DISPLAY variable, I can run xclock or glxgears on any of the three displays.  Using wmctrl I can even make it look like I'm running one glxgears instance across all three displays: [http://idc.mdx.ac.uk/~chris30/gears.wmv](http://idc.mdx.ac.uk/~chris30/gears.wmv)

My problem comes when I try to run Java applications.  Java only sees the 18 individual monitors.  So using the DISPLAY variables :0.0, :0.1, :0.2 the application only moves from one individual window to the next, unlike glxgears, which moves across each group of six monitors (so to monitors 7 and 13 respectively).  What makes things even more interesting is when I have a JOGL instance running inside a swing window.  Using DISPLAY set to :0.1 and 0.2, the swing window moves to monitors 2 and 3, while the OpenGL graphic moves to monitors 7 and 13 (on cards 2 and 3).   Exiting the application completely hangs X and the system needs a reboot.

My question is: is it possible to make Java see only the three monitor arrays. and not the individual monitors?  

A copy of my xorg.conf can be found here, however, it's a bastardisation of automated and manually created content: [http://idc.mdx.ac.uk/~chris30/xorg.conf](http://idc.mdx.ac.uk/~chris30/xorg.conf)

Many thanks
Chris

---

### Post by chris41 on 2013-08-16
A quick update after some more investigation.  It only appears to happen with Swing and AWT. Newt and SWT windows work fine.

---

