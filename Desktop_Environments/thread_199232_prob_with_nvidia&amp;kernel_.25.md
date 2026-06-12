---
title: "prob with nvidia&amp;kernel .25"
date: 2006-06-18
forum: Desktop Environments
---

### Post by 2pacalypse on 2006-06-18
I've got  little prob with my new kernel (something.25), I tried to install graphical  drivers to it but from some reason it didnt worked so i tried to use a back door to it (sudo gedit /etc/X11/xorg.conf) but no luck. it only messed up my system and now im getting an X server error with anything besides the .23 kernel. im gonna try to rewind my changes back but i still need info on how to install the driver for .25 (if it requirest the offical driver please say how to completely exit the X-Server besides getting the X-Server error).



thanks in advance

edit:
i fixed the .25, but i dont have 3d here cuz my video drivers arent install and the nvidia-glx nvidia-kernel things arnt workin

---

### Post by jimisdead on 2006-06-30
I'm having the same problems since upgrading to .25 - I'm running an nVidia 6800 go, and all video is jerky (incredibly annoying), katapult fade in is stuttered down to about 3 or 4 frames (no smooth fade), and the little exploding squares over the icons in konquerer has a very very slow animation now.

I booted from the .23 kernel and now have no problem at all... I hope they fix this in the next kernel update.

---

### Post by tseliot on 2006-06-30
[QUOTE=2pacalypse]I've got  little prob with my new kernel (something.25), I tried to install graphical  drivers to it but from some reason it didnt worked so i tried to use a back door to it (sudo gedit /etc/X11/xorg.conf) but no luck. it only messed up my system and now im getting an X server error with anything besides the .23 kernel. im gonna try to rewind my changes back but i still need info on how to install the driver for .25 (if it requirest the offical driver please say how to completely exit the X-Server besides getting the X-Server error).



thanks in advance

edit:
i fixed the .25, but i dont have 3d here cuz my video drivers arent install and the nvidia-glx nvidia-kernel things arnt workin[/QUOTE]
Try my Envy script

[http://www.albertomilone.eu/europeo/nvidia_scripts1.html](http://www.albertomilone.eu/europeo/nvidia_scripts1.html)

---

