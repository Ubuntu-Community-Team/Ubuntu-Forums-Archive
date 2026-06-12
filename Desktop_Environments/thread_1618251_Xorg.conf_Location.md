---
title: "Xorg.conf Location"
date: 2010-11-10
forum: Desktop Environments
---

### Post by Arcath on 2010-11-10
I have a 3rd party driver that is trying to install a touch screen driver, it is looking in /etc/X11 for xorg.conf and it isnt there. The Ubuntu docs pointed me at a diff folder which also didn't contain xorg.conf.

Where is it located? I will just sym link it during install them remove the link once its done.

EDIT: Should probably mention that I'm running ubuntu 10.10 (Which was upgraded from 10.04). And I'm running Desktop Edition

my /etc/X11
```
[16:35:23][arcath@Constance][~] ls /etc/X11/
app-defaults             fonts    xinit   Xreset.d    Xsession.d
cursors                  rgb.txt  xkb     Xresources  Xsession.options
default-display-manager  X        Xreset  Xsession    Xwrapper.config
```

---

### Post by mcduck on 2010-11-10
The correct place is /etc/X11/xorg.conf, but the file doesn't exist by default in Ubuntu (things are mostly automatically detected instead).

If you need to configure something in that file, just create it and it will be used. :)

---

### Post by Arcath on 2010-11-10
Thanks, the driver installed, doesn't work yet tho :(

---

### Post by Arcath on 2010-11-10
The driver installer rather helpfully modifies the xorg.conf for you adding the touchscreen to the input list etc... unforutunatley it appears that an empty xorg.conf is no good as it has none of the required settings.

Is there a way of generating an xorg.conf that is "what ubuntus using at the moment"

---

### Post by mcduck on 2010-11-10
Yeah, you'll probably need at least the basic configuration options in the file if you create it.

Anyway, this should help: [https://wiki.ubuntu.com/X/Config]("https://wiki.ubuntu.com/X/Config")

---

