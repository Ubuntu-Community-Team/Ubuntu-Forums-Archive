---
title: "vnc problem - same apps dont run"
date: 2007-06-26
forum: Desktop Environments
---

### Post by darkoK on 2007-06-26
I am running vnc4server on Feisty ubuntu, I am running KDE session. I installed debian package becouse ubuntu package was crashing my server. I found instructions here:
[http://badtux.net/labels/technology.html](http://badtux.net/labels/technology.html)  "Making vncserver work on Ubuntu"

 I start vnc4server: vnc4server -depth 16 -geometry 1920x1200 :2

than I connect to it from XP using TighVNC  viewer. Vnc session starts ok but some application run while others don't. They start to load but then nothing happens. It looks that KDE apps load ok while gnome apps don't.  This is my xstartup file:

#!/bin/sh
export KDEHOME="${HOME}/.vnckde"
xrdb $HOME/.Xresources
vncconfig &

thanks

Darko

---

### Post by scxtt on 2007-06-26
not sure how much of a difference it'd make, or if "vncconfig &" takes care of it ... but what if you replace all of those w/ "startkde" ...

#!/bin/sh
startkde &

---

### Post by darkoK on 2007-06-26
It looks that problem was that by mistake I reinstaled ubuntu packages. I now deinstalled them and installed debian version again. It all works now.  So for me vnc4server debian works better

[http://packages.debian.org/stable/x11/vnc4server](http://packages.debian.org/stable/x11/vnc4server)
[http://packages.debian.org/stable/x11/vnc4-common](http://packages.debian.org/stable/x11/vnc4-common)

Thanks

Darko

---

