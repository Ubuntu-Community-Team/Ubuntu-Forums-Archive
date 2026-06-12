---
title: "Ubuntu 9.04 and Compiz prolems."
date: 2009-04-26
forum: Desktop Environments
---

### Post by schmidty313 on 2009-04-26
So I just uninstalled wubi 8.10 and installed wubi 9.04.  I am happy with the increased boot speed and overall look, but I am having problems with Compiz.  I installed Compiz ccsm and compiz manager icon.  I can get it to work, but when I reboot, I have to reload the window manager using the icon.  If I dont, it will just tun the normal desktop with no effects such as the desktop cube.  How can I fix this to run at startup?

compiz -check:
```
erik@ubuntu:~$ compiz -check
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity 
metacity: Unknown option -check

```

btw: compiz worked fine on 8.10

Dell vostro 1510
3GB sys ram
Intel Corporation Mobile GM965/GL960 Integrated Graphics
Thanks!

---

### Post by andrea000 on 2009-04-26
I just did this about 24 hours ago but i followed this guide
on 8.10 and mine works fine i am not using a blacklisted card 
but compiz was picking up on my integrated card anyway have a 
look [here]("http://www.searchmarked.com/ubuntu/how-to-enable-compiz-fusion-on-ubuntu-710-if-your-video-card-is-blacklisted.php")
it says 7.10 but works on 8.10 to maybe 9.04

---

