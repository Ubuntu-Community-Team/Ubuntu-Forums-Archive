---
title: "Display problems on new install"
date: 2005-12-17
forum: Desktop Environments
---

### Post by stephenry on 2005-12-17
Hello,

I've just install Ubuntu over my gentoo install, and I'm having some difficulty getting my xserver to work properly.

After spending about an hour trying to modify my xorg.conf file to produce a resolution of 1600x1200@85Hz, I have a new problem. I cannot get my screen to match the dimensions of the monitor; I have two vertical black bars running down either side of my screen. Ordinarily, I would have attempted to alter my monitors configuration, but my monitor is already configured so that my screen is as wide as it can be made. It cannot be made any wider.

I thought that this would be a driver issues so I installed the latest nvidia drivers. Now I have an additional problem: when I try to run glxgears (to test the opengl capabilities of my system) I get the error message:

Xlib: extension "GLX" missing on display ":0.0"
Error: couldn't get an RGB, Double-buffered visual

I have no idea what the problem is. I'm assuming that because I can get 1600x1200@85Hz I'm pretty close to the solution, but there's something I'm missing.

Any ideas?

Stephen

---

### Post by tuxy on 2005-12-17
If nothing works try " dpkg-reconfigure xserver-xorg". I had the same problem & it worked. Make sure you restart the pc after you do this/restart x.

---

