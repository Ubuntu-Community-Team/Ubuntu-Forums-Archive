---
title: "possible to remove  login screen, but nothing else"
date: 2008-11-07
forum: Desktop Environments
---

### Post by BetterSense on 2008-11-07
I have a slow laptop and I'm optimizing total boot time. I want to remove the graphical login screen, because I think just typing startx would be faster rather than loading the login screen just to type in my password. I thought the only thing gdm did was the login screen, but running ```
apt-get remove gdm
``` threatens to remove gnome-fast-switcher-applet and ubuntu-desktop! 

Is there a way to do this? If I remove the login screen, how can I boot KDE if I ever want to?

---

### Post by bionnaki on 2008-11-08
use a lighter manager like slim
[http://packages.ubuntu.com/intrepid/slim](http://packages.ubuntu.com/intrepid/slim)

---

