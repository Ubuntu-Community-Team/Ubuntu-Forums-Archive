---
title: "dual screens: need mirror image, not extra desktop"
date: 2010-09-08
forum: Desktop Environments
---

### Post by finite9 on 2010-09-08
I'm using an Intel chipset GMA4500 and Ubuntu 10.04 Gnome.  The monitor configuration tool does not seem to have an option to make the secondary screen a mirror image of the primary screen.  It works fine when I connect my TV using HDMI as a second screen, but I want it to be a mirror of the primary, because some apps like Skype will only go "full screen" on the primary display.

Does anyone know how I can achieve this?

---

### Post by TwelveGauge on 2010-09-08
System -> Prefs -> Monitors -> Mirror images on both monitors

---

### Post by finite9 on 2010-09-11
for some reason that option al always greyed out whether the TV is connected or not.

I looked into xrandr, but it seems to conflict with the Monitor tool that gets automatically activated when I connect te TV using HDMI.

I understand that I have to "clone" my laptop screen to the TV, as a mirror assumes that the resolution and refresh rate is the same on both screens, which isn't the case.

From what I gather, the following will do a clone, but I lose my Laptop screen:

```
xrandr --output HDMI1 --auto
```

I have yet to test this to see if it conflicts with the monitor tool.

---

