---
title: "[SOLVED] 3D Screensaver of Death - FIXED!"
date: 2007-07-24
forum: Dell  Ubuntu Support
---

### Post by projektdotnet on 2007-07-24
Ok so I boot my brand spankin new 1420N and when I try to enable any 3d screensaver it locks up X and only responds to power button from then on until I reboot. Here's the quick fix until a true solution is found.

```

$ sudo apt-get remove gnome-screensaver xscreensaver-gl
$ sudo apt-get install xscreensaver
$ xscreensaver

```

The xscreensaver configuration window will pop-up, I chose to set mine to blank the screen but feel free to find one you like.

Hope this helps someone.

---

### Post by sciurus on 2007-07-24
Alternately, you can clear /app/gnome-screenaver/themes in gconf.

---

