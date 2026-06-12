---
title: "Dual monitor gaming woes (Full-Screen support crashing Gnome!)"
date: 2006-01-08
forum: General Help
---

### Post by Stelmate on 2006-01-08
Currently I'm using the nvidia driver's TwinView with dual monitors, gnome and xfwm4.
When I use any games that require full screen support it doesn't work and crashes the game.  Gnome will try to open up the game on one screen but the game either crashes Gnome or just locks up.  I have tried the TuxRacer,Planeshift,Quake4 demo, and Nexuiz.. does anyone know a workaround for this?? All these games worked before I had the dual-monitor setup and I would really like to keep the dual monitors.

---

### Post by Stelmate on 2006-01-11
Solved:

If anyone is having problems with their dual monitors (and they have a nvidia card) here is the solution:

Follow this tutorial:
[http://gentoo-wiki.com/HOWTO_Dual_Monitors](http://gentoo-wiki.com/HOWTO_Dual_Monitors)

Also, make sure that your monitor connected to the DVI port is to the left of the VGA, otherwise full-screen games/apps will come out wrong.  Make sure when defining the metamodes that you define not only a set for each monitor
(i.e. 1280x1024,1280x1024; )
but also a extra metamode for 1 monitor by itself
(i.e. 1280x1024,1280x1024; 1280x1024;)
otherwise fullscreen games will crash X...

And make sure and turn off Xinerama when you use TwinView.. (its in the above tutorial)

---

