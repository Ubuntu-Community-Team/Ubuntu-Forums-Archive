---
title: "KDE gets resolution, gnome doesn't"
date: 2007-06-14
forum: Desktop Environments
---

### Post by papatrpt89 on 2007-06-14
Hello,

Yesterday I got a brand new, spiffy pc.

I have gotten beryl working under both KDE and Gnome.

However, KDE correctly detects my native resolution of 1280x1024, and displays it perfectly.  Under gnome, I can get no higher than 1024x768 under system, preferences, screen resolution.

GPU: Nvidia 8600GT, with beta drivers installed and working correctly.

When I try messing with resolution in gnome with sudo nvidia-settings, it will display, but many, many things are screwed up.  Any advice?

btw, a BIG thanks to everyone in beryl for making such an amazing program!

---

### Post by DonnieP on 2007-06-14
I don't know why KDE would get it and not GNOME, but you should be able to fix GNOME by re-running sudo dpkg-reconfigure xserver-xorg.

---

### Post by papatrpt89 on 2007-06-14
After a whole lot of messing around, I got things to work.  Thanks for the tip!

What I found to work was this: I ran gksu nvidia-settings and changed the resolution there.  Then, I restarted x.  It would login on the wrong resolution again, then I would change it inside of system, preferences, screen resolution.  Now I'm running in gnome at a nice 1280x1024.  Thanks!

---

