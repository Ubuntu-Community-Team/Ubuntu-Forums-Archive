---
title: "Screensaver engages even though it's disabled?"
date: 2011-09-21
forum: Desktop Environments
---

### Post by netslacker on 2011-09-21
I need a display-only kiosk (cpu and monitor only) for a project and I've been using ubuntu 11.04 as the basis.  When I disable the screen saver via gnome things are fine however, since I don't want a keyboard and mouse, once I remove them the screensaver process starts after 10 minutes and the screen appears to freeze.  If I plug in the mouse and give it a little bump then things resume.  So long as a mouse is plugged in it will never freeze (screensaver start).  I need the screensaver completely disabled or even removed so that there's no chance of this even without a keyboard/mouse attached.

Any ideas on how I would do this?

Thanks in advance.

---

### Post by SecretCode on 2011-09-21
You could try removing package gnome-screensaver - although what you describe sounds like a bug and ought to be reported. If it hasn't already been.

---

### Post by netslacker on 2011-09-21
I tried that.  If I remove gnome-screensaver then the scenario I described that occurs when no mouse is connected happens when a mouse is connected.  If I install gnome-screensaver then at least it is disabled w/ the mouse.  Now just need to figure out how to disable it w/o a mouse...

---

### Post by SecretCode on 2011-09-22
A bit odd.

What timeouts do you have in power management preferences?

---

### Post by stinkeye on 2011-09-22
See [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1483345&page=2")
to see if you are using **DPMS (Energy Star)** and for a fix.

---

### Post by netslacker on 2011-09-24
Using the xset commands seems to have solved my problem, thanks Stinkeye!

xset s off
xset -dpms

---

