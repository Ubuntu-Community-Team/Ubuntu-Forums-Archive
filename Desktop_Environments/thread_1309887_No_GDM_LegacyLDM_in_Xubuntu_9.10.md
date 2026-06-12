---
title: "No GDM Legacy/LDM in Xubuntu 9.10"
date: 2009-11-01
forum: Desktop Environments
---

### Post by icenight on 2009-11-01
Hey guys, i've been trying for the last couple of hours to get gdm 2.20 or ldm working on my xubuntu 9.10 install. I hate the way the new gdm looks/the fact that I can't really theme or customize it, and it takes too long to log me in, slowing down my system. I've even gone so far as to backup the home folder from my previous install/upgrade (9.04 to 9.10) and do a fresh install, still with little success. When I install wdm or gdm in synaptic, a debconf windows pop's up, but ldm isn't listed and gdm-2.20 when selected doesn't work after a reboot. I have to logon from terminal and issue startx. HELP ME!!!!
 
All suggestions are appreciated.

---

### Post by earthpigg on 2009-11-01
hi,

i've been having similar difficulties.

[http://ubuntuforums.org/showthread.php?t=1299214](http://ubuntuforums.org/showthread.php?t=1299214)

---

### Post by icenight on 2009-11-04
I ended up installing slim from the debian repositories and all is well... it's a great login/display manager, very light on resources too.

---

### Post by Carnophage on 2009-11-07
> **icenight said:**
> I ended up installing slim from the debian repositories and all is well... it's a great login/display manager, very light on resources too.
Did You do something more then just install slim? I took a try and ended with a blank screen (just like when I tried gdm-legacy)

---

### Post by icenight on 2009-12-02
to get slim working (if you haven't given up already) I had installed wdm from the ubuntu repositories first, trying out any login browser I could find.  It looked crappy, so I looked for alternatives and found slim.  It wasn't in the ubuntu repositories, so I downloaded the lastest .deb from the debian ones instead.  Installed it, with all dependencies auto-style, and the went back into terminal and issued command "dpkg-reconfigure wdm" and when the login config box popped up, selected slim.  After I restarted and slim came up, I logged in and removed wdm.  You don't have to use wdm, and installed logon manager will work as long as you issue the command "dpkg-reconfigure %yourgdm%" and select slim.  This is will probably be useful to anyone who stumbles on this thread in the future.

---

