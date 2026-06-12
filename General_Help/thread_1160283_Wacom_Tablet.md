---
title: "Wacom Tablet"
date: 2009-05-15
forum: General Help
---

### Post by measekite on 2009-05-15
I amusing a Wacom tablet that has both a pen and a mouse.  They are both working.

I would like to  be able to set the speed of the mouse and the double click speed.

The standard mouse applet sets these items for my standard Logitech mouse.

**Where would I find the settings to adjust the Wacom mouse and other preferences.  I do not see a Wacom entry in the menu.**

---

### Post by Favux on 2009-05-19
Hi measekite,

You configure and calibrate Wacom with the configuration gui "wacomcpl".  Check in Synaptic Package Manager that wacom-tools is installed.  "Wacomcpl" generates a file, ".xinitrc", which you can also edit directly.  To use type in a terminal:
```
wacomcpl
```
For more on using it see Section 3 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

I don't know if you can change the Wacom mouse's double click speed.  I think the speed of the mouse can be changed with this xsetwacom command:
```
SpeedLevel    integer (1 - 11)         sets relative cursor movement speed

```
From here:  [http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom)

I hope this helps.

---

