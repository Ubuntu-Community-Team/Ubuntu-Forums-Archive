---
title: "Changing Login Screen Format."
date: 2012-12-19
forum: Desktop Environments
---

### Post by doxramos on 2012-12-19
Okay, so on Ubuntu 10.04 I like almost everything. One thing I don't like is the layout and color scheme of the login screen. I know how to change the images in the login screen however it still leaves me with a white border around my username and with it being in the center of the screen. My thought was to move it over to the left and give it a transparent/black tinted border and then actually resize the border. Does anyone know how I can accomplish this?

---

### Post by RitzBitzN on 2012-12-19
If you want to change the background, type in: gksu "nautilus --no-desktop /usr/share/gnome-shell/theme/" and replace nois-texture.png with whatever you want to put there. As for the rest, try using GDM3Setup ([https://github.com/Nano77/gdm3setup](https://github.com/Nano77/gdm3setup)). I use KDE, so I haven't ever really played around with it, but I hear that it is very flexible.

---

### Post by doxramos on 2012-12-19
Unfortunately GDM3 doesn't seem to work with 10.04; I'm trying to find a way to install it from the source on github, but I have no idea what I'm doing ha.

---

### Post by Frogs Hair on 2012-12-19
I think 10.04 still had an application called startup manager that allowed for login screen customization.

---

### Post by doxramos on 2012-12-20
It does have Startup Manager, but that has nothing as far as login screen customization goes. Just the bootloader from the looks of it.

---

