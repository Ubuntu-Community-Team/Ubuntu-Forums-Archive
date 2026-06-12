---
title: "XFCE and Horizontal Scrolling"
date: 2010-10-18
forum: Desktop Environments
---

### Post by Wellconnected on 2010-10-18
Hello All,

I have a synaptics touchpad, vertical scrolling is fine.

If I set up horizontal scrolling in gsynaptics, and scroll along the bottom, the mouse does not move (it seems to be correctly in horizontal scroll mode) but the command does not seem to be passed onto the selected window: no scrolling.

What do I need to do?

Xubuntu 10.04

E

---

### Post by liquider on 2011-02-19
I apologize for reviving this old thread, but I was facing the same problem, and Google pointed me to this unsolved thread.

What worked for me and made XFCE respect my horizontal scrolling setting is: **install gpointing-device-settings**, run it from terminal and configure it.

HTH, :)

---

### Post by Kremlin on 2012-02-19
This solution works for me, but I have to re-apply it every startup. I also have to run "syndaemon -i 2 -d -t -K" to prevent my palm from moving the touchpad while I am typing text.

Is there any way to make this setting "stick" so that I don't have to run these two commands every startup? I've looked in gconf but it doesn't seem to matter whether Desktop/gnome/peripherals/touchpad (or the Synaptics one in the same root) has horizontal scrolling enabled or disabled - the only thing that changes anything is running the gpointing-device-settings manager and re-checking the option there.

---

### Post by Copper Bezel on 2012-02-19
There's a file, /usr/share/X11/xorg.conf.d/51-synaptics-quirks.conf, where you can make changes to the Synaptics defaults. You'll want to add a section like this:

```
Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Option "SHMConfig" "on"
        Option "HorizEdgeScroll" "1"
        Option "PalmDetect" "1"
EndSection
```

---

