---
title: "KDE not starting"
date: 2005-09-03
forum: Desktop Environments
---

### Post by arcanistherogue on 2005-09-03
Hey.  I recently upgraded all of my packages and installed some firefox ones.  When I rebooted, it said it couldn't find the nvidia driver, so i switced to the generic one ("nv", it was there before I changed it to "nvidia").  When I did startx, it loaded gnome.

After upgrading nvidia-glx then changing it back to the nvidia driver, it loaded up to the kde login screen.  When I got here, I tried to log in but I got an error and was returned to the login screen. 

the error is:

> The following installation problem was 
detected while trying to start KDE

(this part is indented) No write access to '/home/john/.ICEauthority'.

KDE is unable to start.

then, when I dismissed this message, i got one more before being returned to the login screen.  

> 
could not start kmserver.  Check your installation.

now, even GNOME wont work.  I dont get an error, it just brings me straight back to the login screen. 

How do I fix this?

---

### Post by mlomker on 2005-09-04
Have you tried **chown -R john ~/.ICE* ~/.kde**?

---

