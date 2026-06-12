---
title: "Xinerama Dual-Monitor problem"
date: 2006-06-06
forum: Desktop Environments
---

### Post by Gamma_Ray54 on 2006-06-06
Hey all.  I've got an ATI dual-head card and am trying to get multiple monitor support working.  I managed to edit my Xorg.conf file so that I get two separate monitors (separate X sessions), but I want one desktop that extends between them.  I know that I can either do this through the ATI-specific driver options (Option "DesktopSetup" "horizontal") or through Xinerama.  The driver-specific option works, however the window manager doesn't seem to know about the separate screens, so windows maximize across both monitors, etc.  So I tried to use Xinerama.  I added Option "Xinerama" "true" to the ServerLayout section of Xorg.conf, however when I restart X I run into problems.  I can move the mouse onto the second monitor, however the contents of the monitor other than the mouse pointer are simply mirrored off of the first monitor.  However, the desktop size in the workspace switcher shows up as a double-wide screen, and I can maximize a window over the first monitor, or drag it over to the space where the second monitor should be, and maximize it there, I just can't actually see it.  So the window manager knows about the screen boundaries and everything, but for some reason it's not actually performing the rendering on the second monitor.  Anybody have any ideas what could be going on?

---

