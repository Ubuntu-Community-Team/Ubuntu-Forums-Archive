---
title: "Dual Monitors: How...."
date: 2009-09-20
forum: Desktop Environments
---

### Post by chome4 on 2009-09-20
I have a VGA and HDMI monitor. The VGA is the one with the Ubuntu menu along the top along with the power on/off icon.

How can I tell Ubuntu to 'swap' so that my HDMI monitor is now the one with the above menu and power button on show? Basically, I want to change my primary monitor.

---

### Post by nperry on 2009-09-20
> **chome4 said:**
> I have a VGA and HDMI monitor. The VGA is the one with the Ubuntu menu along the top along with the power on/off icon.

How can I tell Ubuntu to 'swap' so that my HDMI monitor is now the one with the above menu and power button on show? Basically, I want to change my primary monitor.

Launch 'gnome-display-properties' from terminal. Select the HDMI monitor and there should be set as default or primary - Can't remember what it actually says

---

### Post by chome4 on 2009-09-20
This is what I've been using as my first effort. There is no reference to 'primary' monitor.

This should be the way to do it!

---

### Post by jenkinsororo on 2009-09-20
I don'y know, I'm pretty new to Ubuntu and it's pretty much all greek to me :(

---

### Post by SuperSonic4 on 2009-09-20
What does ```
lspci | grep VGA
``` come up with?

---

### Post by chome4 on 2009-09-20
lspci | grep VGA

gives:

01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]

---

### Post by bobince on 2009-09-22
Unfortunately it does not seem to be possible to redesignate the ‘primary’ monitor (at least on my setup with intel graphics).

However you can easily move your GNOME panels to the secondary monitor, and then most things launched from them will appear on the correct monitor. Some programs may still, annoyingly, launch on the primary and have to be moved. This may be a window manager problem as much as an application one; it used to happen for me with Firefox dialogue boxes on Jaunty with metacity, but it seems OK now under Karmic with compiz.

The trick to moving panels is to right-click-Properties and untick the ‘Expand’ option. Now you can see the panel's drag handle, which you can use to push it into position on the other display. Then edit Properties again to turn Expand back on. (This is something GNOME should really make more obvious IMO.)

---

