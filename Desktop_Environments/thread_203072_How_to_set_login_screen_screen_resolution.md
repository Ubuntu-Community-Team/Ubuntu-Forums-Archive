---
title: "How to set login screen screen resolution?"
date: 2006-06-24
forum: Desktop Environments
---

### Post by Hop-Frog on 2006-06-24
I set my computer to 1024x728 screen resolution.  However, when at the login screen, the screen resolution is much higher, one that shows up, but that is not recommended by my monitor manufacturer.  I looked in /etc/X11/xorg.conf, but I do not understand how to set the screen resolution here.

Thanks.

---

### Post by Ramses de Norre on 2006-06-24
Look at the Modes line in the screen section and remove all modes higher than the one you want, best thing is to do this for all color depths.

EDIT: use sudo gedit /etc/X11/xorg.conf to edit the file.

---

