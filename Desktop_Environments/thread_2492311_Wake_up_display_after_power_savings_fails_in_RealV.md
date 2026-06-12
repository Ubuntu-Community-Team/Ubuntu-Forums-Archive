---
title: "Wake up display after power savings fails in RealVNC Viewer"
date: 2023-11-07
forum: Desktop Environments
---

### Post by bert.ram.aerts on 2023-11-07
I use Ubuntu 23.10 with XFCE 4.18 on a Lenovo Legion 5 laptop.
In BIOS discrete graphics is set with nVIDIA GeForce RTX-2060, so no Intel graphics.
I use X11 and not Wayland.
I use RealVNC Server 7.7.0 on Ubuntu XFCE laptop.
I use RealVNC Viewer 7.7.0 on a Windows 10 laptop to connect with Ubuntu XFCE.
Power Manager settings in XFCE for Display in "Plugged in" state are
+ blank after 10 minutes
+ put to sleep after 11 minutes
+ switch off after 12 minutes
Problem is that when XFCE display is switched off due to power savings and I see a black screen in VNC Viewer, I can move the mouse of the Windows laptop and in VNC Viewer I see the XFCE display again, but everything is extremely slow. When I look at the XFCE laptop, display is still off, so I did not succeed in waking up the XFCE display. As soon as I move the mouse of the Ubuntu laptop with XFCE display, display goes on again. From that moment onwards VNC viewer on the Windows laptop reacts normal on mouse/key commands.


Before I started using XFCE, I was using Gnome and there this display-no-wake-up-issue does NOT exist.


Questions:
Is there a keyboard key combination on the Windows laptop to get the XFCE display switched on again?
Or is there another solution?


I know that RealVNC advises to turn OFF power savings on the machine running VNC Server.
But as it was working in Gnome, I hope to get it also working in XFCE.

---

