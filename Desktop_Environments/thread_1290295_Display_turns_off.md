---
title: "Display turns off"
date: 2009-10-13
forum: Desktop Environments
---

### Post by danielwinter on 2009-10-13
Hello There!
I'm new to Ubuntu and have installed it on my older P4 with intel integrated graphics.

Everything works fine, but sometimes the display fades to black (while the display LED is still green, indicating its turned od), after shutting off and on the display, it works again for a few seconds, but it turns black again. I don't know what it could be.. the screensaver is set to come after 1 hour.  I have already turned off the energy saving mode (because the pc didn't wake up).

One little correction that could be done too: The display has the wrong resolution.. it's native reso is 1280*1024, but ubuntu display it as the 1152*864 thing.. I haven't got the 1280 available, any suggestions?

---

### Post by TommyMac501 on 2009-10-13
Try going to "system' -> 'Power Management Preferences' and see what the setting for 'Put display to sleep when inactive for' is set to.  You can set it to 'Never'.  Hope that helps.

TM

---

### Post by danielwinter on 2009-10-13
thanks a lot for the fast reply,
but no, the setting is already set to "never" :(

---

### Post by karlson on 2009-10-13
> **danielwinter said:**
> thanks a lot for the fast reply,
but no, the setting is already set to "never" :(

You may have to put the specific configuration into the /etc/xorg/xorg.conf for your monitor for the resolution and settings.

---

### Post by danielwinter on 2009-10-13
i think you meant /etc/X11/xorg.conf, because i'm not finding the other folder.
this file is quite empty, does anyone have any suggestions to fill in?

---

