---
title: "xrandr outside X: crtc error"
date: 2013-01-31
forum: Desktop Environments
---

### Post by Kraut~salat on 2013-01-31
hi all,
i wanted to write a script using xrandr which autoamtically switches monitor settings whenever I dock or undock my notebook from its dockingstation: 
undocked -> notebook screen only (obviously!)
docked -> notebook screen off, external screen at DVI port only

I have an old thinkpad T60 with deditaced ATI graphics X1400 running X with the open source radeon driver.

The scripts I wrote work when I run them in a terminal under X:
```
xrandr --output LVDS --off --output DVI-0 --auto
```
for example for "docked"-mode.

But when switching to the console outside X with Ctrl+Alt+F1 xrandr does not work anymore. First, it does not find the display anymore I have to supply it with the ```
-display :0.0
``` option. But even then it complains saying ```
configure crtc 1 failed
```. Using the --crtc option with either 0 or 1 does not help either.

The way I wanted to initiate monitor switching was via a udev-rule that starts a shell script containing the xrandr command whenever the dock-state changes. But that does not work, because xrander doesn't work properly outside of X.

So question 1: Does anyone know a way to get xrandr to work?
question 2: Is there an alternative way to accomplish this? Something like "let the udev rule start a shell script that sends a message on the dbus which an XFce app listens for an then starts the monitor switching from inside X." This is more complicated and I don't know anything about dbus or the likes. But if that is the only way I'll have to do that.

Thx

---

### Post by Kraut~salat on 2013-01-31
> **tarqeb said:**
> [COLOR=Blue]hi guys .......
plze.[.]("http://www.tarqeb.com"). help ......[/COLOR]

yeah.. right..

---

