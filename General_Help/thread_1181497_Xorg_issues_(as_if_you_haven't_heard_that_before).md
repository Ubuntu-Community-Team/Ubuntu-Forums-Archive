---
title: "Xorg issues (as if you haven't heard that before)"
date: 2009-06-08
forum: General Help
---

### Post by jeffrey296 on 2009-06-08
Hi. I recently used an SVideo cable to connect my laptop to my TV because I couldn't find my SVGA cable. I'm running Ubuntu 9.04, and yes I probably upgraded just a bit too soon. Basically the dual-screen setup would work at the login screen but failed after logging in. My guess is that it failed once it reached the xorg.conf file. Now I've disconnected the SVideo cable and this is some time and numerous restarts after that and my screen resolution is off. The resolution is *perfect* at the login screen (maybe due to the fact that my login screen is custom?), but after logging in it changes to 1024x768. I've tried switching to one of my numerous xorg.conf backup files to no avail. I've also tried automatically detecting settings (dpkg-reconfigure xserver-xorg) while the xserver was off (/etc/init.d/gdm stop), but this still did not work. Oh yeah and I'm running Gnome if that matters much.

I do not know what my exact resolution is, and I tried manually investigating the login window themes but could not find anywhere where it set the resolution. The GUI for the screen resolution only allows me to go up to 1024x768.

Any help would be appreciated thanks,
Jeff

---

### Post by Legace on 2009-06-08
Open Terminal, type in **xrandr** and post output here.

---

### Post by jeffrey296 on 2009-06-09
xrandr output per request:

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1280 x 1280
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0 +
   1024x768       85.0*    75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TV disconnected (normal left inverted right x axis y axis)

Thanks for the fast response time.
Jeff

---

