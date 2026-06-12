---
title: "How to set the step-size for the gnome-shell magnifier?"
date: 2012-06-05
forum: Desktop Environments
---

### Post by Bazon on 2012-06-05
For me, the gnome-shell magnifier makes too big steps between the different degrees of magnification.
I hoped to be able to set it in dconf, but in org.gnome.desktop.a11y.magnifier was no way to control the step-size.
So where is it actually set?

---

### Post by stinkeye on 2012-06-06
Try **gnome-shell-mousewheel-zoom** from this ppa
[**_[COLOR="DarkRed"]https://launchpad.net/~tobias-quinn/+archive/gsmz/+packages[/COLOR]_**]("https://launchpad.net/~tobias-quinn/+archive/gsmz/+packages")

After install log out/in and should have an alt+mousewheel zoom

---

### Post by Bazon on 2012-06-06
Thanks, but it doesn't work for me. Alt + Mousewheel has no result. :-(
(Although it installed flawless.)

---

### Post by stinkeye on 2012-06-06
I found this ppa from this [**_[COLOR="DarkRed"]ARTICLE[/COLOR]_**]("http://www.webupd8.org/2011/09/compiz-like-mousewheel-zoom-tool-for.html")
PPA was in the comments.

I don't usually use gnome-shell but the zoom works when I log into the **gnome** sesssion.

All I can tell you is that before installing **mousewheelzoom**,
the Universal Access zoom was turned off with no shortcuts set.
Remains the same after install.

The **gnome-shell-mousewheel-zoom** package installs a
**mousewheelzoom.desktop** file in **/etc/xdg/autostart** so should autostart in the gnome session.
Do you have a **mousewheelzoom** process running in system monitor.
If not try running...
```
/usr/bin/mousewheelzoom
```

---

### Post by Bazon on 2012-06-06
Yes, the process is running. 
Following your article, I installed
```
sudo apt-get install python-xlib python-dbus git-core
``` (missed before), restarted Gnome-Shell ```
r
```, logged out and in again, but alt+mousewheel does nothing... :-(

thanks anyway!

---

