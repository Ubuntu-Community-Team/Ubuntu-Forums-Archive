---
title: "Xorg fixed font not found"
date: 2006-09-06
forum: Desktop Environments
---

### Post by n_hendrick on 2006-09-06
I rebooted my pc and what do you know the xserver spit 
out a can't find fixed font error. I've been googling
for about 4 hours now and still haven't been able to come
to a solution. I've tried installing symbolic links 
between font directorys. I must of change my xorg file
three dozen times by now and I still can't get X
to load. I've tried fc-cache, I've tried installing the 
new xfonts packages, I even did a total system 
recopnfiguration....still know go. I'm at odds here, 
hopefully someone on this website will know what I'm
overlooking. Help me please.

---

### Post by n_hendrick on 2006-09-07
problem has been solved. I just had to completely purge out the packages: xfonts-base x-window-system-core ubuntu-desktop...and re-install those packages, then for some reason the system just started working again..........load off my head, I didn't want to do a complete re-install.

---

