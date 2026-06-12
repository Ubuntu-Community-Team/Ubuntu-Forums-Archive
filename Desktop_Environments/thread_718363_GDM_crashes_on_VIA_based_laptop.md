---
title: "GDM crashes on VIA based laptop"
date: 2008-03-08
forum: Desktop Environments
---

### Post by Trimesh on 2008-03-08
Maybe someone could shed some light on this - I have a VIA based subnotebook with a WSVGA (1024x600) LCD panel.  I've installed 7.10 using the alternate install CD (since the live CD couldn't bring the desktop up).

If I set the resolution in X to 800x600 using the vesa driver, it all works correctly - GDM comes up, I can log in and the desktop loads.

If I change the resolution to 1024x600, then GDM gets into a crash / respawn loop until I power down.

The strange thing is that if I boot up in 800x600, Ctrl-Alt-F1 out to the command prompt, edit xorg.conf to 1024x600 and run the X server with X :1 it works.

It also works if I start up in recovery mode and start X with startx - the desktop comes up normally in 1024x600.

Looking through the forums, it looks like the normal suggestion is to change the video driver - but the more I look at this, the more it looks like a bug in GDM, since X is clearly working with no problems on this display at  the correct resoultion.

I had a look at /var/log/Xorg.0.log and /var/log/gdm/:0.log, but they don't seem to contain any useful information.  There appears to be nothing relevant in syslog, either.

Anyone got any ideas?

---

