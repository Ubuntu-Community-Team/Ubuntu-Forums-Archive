---
title: "Missing window borders"
date: 2008-03-25
forum: Desktop Effects &amp; Customization
---

### Post by tonix123 on 2008-03-25
Hi. I've just installed Ubuntu 7.10, 32bit. Everything pretty much works, except for two things. (I have 8800GT, 169.12 driver, got it from nvidia site)

Problem #1 Once I enable visual effects (Compiz if you may, the cube and wobbly windows and that stuff), the window borders and titlebar (the thing with application names and close/minimize/etc buttons) goes away. Also the terminal is a blank page, yet again that *might* be a font/color problem.

* I tried checking and unchecking window borders in Advanced Desktop Effects Manager
* Tried installing Emerald
* Played around with GL Desktop

It doesn't help. The only thing that gives me back my window borders is turning off compiz. (Selecting None at Appearance -> Visual Effects)

I tried running compiz --replace and emerald --replace, just for the sake of it, still nothing.

I even reinstalled the drivers numerous times, which led me to problem #2. After each reboot my xorg.conf settings seem to reset. (I have tried dpkg-reconfigure xserver-xorg before driver install, and afterwards let the nvidia xconfigure utility do it's work), however if I just start the X after the driver setup, everything works just fine (except for the #1 problem).

My rig:
ASUS P5KR Motherboard
2GB RAM
Intel C2D E6750 2.66GHz
and the mentioned 8800GT

I don't have any log info or screenshot at the moment, but I will get back to it asap and provide any information that could be of use to fix this problem.

Thank you very much in advance.

---

### Post by unoodles on 2008-03-25
Had the same exact problem. What i did to fix it was rather complicated. Anyway here goes:

1 create a brand new user.
2 logout and then log into that use. try enabling visual effects. if it does not work then ignore the rest of this guide.
3 if it works, open nautilus as root, and copy all files in your new users home folder and copy them over you original users home folder. (YOU WILL LOSE ALL PANEL SETTINGS!).
4 make sure you clicked replace and not ignore when it asked to overwrite.
5 logout and login to you original user.
6 it should work, kill the recently created user and you're done

---

### Post by Therion on 2008-03-25
Assuming you don't want to use Emerald as your window decorator, the following will solve the problem - permanently:```
mkdir -p ~/.config/compiz/ && echo USE_EMERALD="no" >> ~/.config/compiz/compiz-manager
```

---

