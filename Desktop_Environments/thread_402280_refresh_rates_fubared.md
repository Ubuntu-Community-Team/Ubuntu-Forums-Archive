---
title: "refresh rates fubared"
date: 2007-04-05
forum: Desktop Environments
---

### Post by boast on 2007-04-05
Going to "screen resolution", it seems that at 

50hz = 85hz
53hz = 75hz
55hz = 69hz

[img]http://img53.imageshack.us/img53/8256/img0495wc5.jpg[/img]

---

### Post by calraith on 2007-04-08
In your xorg.conf, try commenting out HorizSync, VertRefresh, and Modeline (if it's there) in Section "Monitor."  Then either reboot or sudo killall -9 gdm, log out, ctrl-alt-backspace to kill X, log into console and sudo gdm to restart X.  Any change?

---

### Post by boast on 2007-04-08
still the same.

---

### Post by calraith on 2007-04-08
Which video driver are you using?  If you're using "vesa" or the xorg-included-by-default "ati" or "nv," maybe your video driver doesn't support the method of auto detection for refresh / sync?  Is there an updated driver available?

---

### Post by boast on 2007-04-08
I'm using the beta nvidia drivers (for a GF2)

---

### Post by calraith on 2007-04-08
Try:

```
sudo killall -9 gdm (or kdm or whatever)
```Log out of your session, then hit Ctrl-Alt-Backspace to go to console.  Log in, then do the following:

```
sudo -s
X -configure
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.whatthecrapiswrongwithxorg
mv xorg.conf* /etc/X11/xorg.conf
gdm (or kdm or whatever)
```Same thing?  By the way, if that screws something up and you lose your ability to start X entirely, you can either Ctrl-Alt-F1 to go to a console, or gdm (or kdm or whatever) will just gracefully crap out and give you a console.  Then you can log in and restore your previous X configuration with the following command:

```
sudo mv /etc/X11/xorg.conf.whatthecrapiswrongwithxorg /etc/X11/xorg.conf
```Any luck?

---

### Post by mannheim on 2007-04-08
When using recent versions of the nvidia driver, the "Screen Resolution" preference setting in the System-->Preferences menu reports incorrect values for the refresh rate. This is a known problem, in that it is mentioned in the readme file for the nvidia driver.

The solution (for now) is to ignore whatever you see under "Screen Resolution". The reliable way is to use nvidia's own utility, "NVIDIA X Server Settings", which is probably installed under Applications-->System Tools. In this utility, look at "X Server Display Configuration". That'll tell you what refresh rate you have, I think.

---

