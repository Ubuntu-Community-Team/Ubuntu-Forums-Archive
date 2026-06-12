---
title: "previously maximized windows open too large for screen"
date: 2008-01-24
forum: Desktop Effects &amp; Customization
---

### Post by andrewkk on 2008-01-24
Some windows, instead of opening properly maximized, open unmaximized but slightly too large to fit on the screen. See the attached screenshot.

This seems to happen to programs that were maximized previously when they were last closed. Upon reopening, the content of the window is sized to fill the screen as if it were maximized, but then window decorations are added around this, making the whole thing too large to fit on the screen. These windows are not centered, but aligned with the top left corner so that they hang off of the bottom right edge of the screen.

I've noticed this happen with at least Nautilus, Gedit and Amarok.


I couldn't find anything on Launchpad mentioning this. Is it likely to be a bug with Compiz or the affected programs, or just something unusual I've done to make this happen?

---

### Post by Ingenium on 2008-01-25
I'm having the same problem, except the windows always hang just off the bottom of the screen.

---

### Post by kryth on 2008-01-25
Trying going to Compiz's settings, go to Placement mode. And play with the settings. I changed the mode from 'smart' to 'centered' and it fixed this problem for me.

---

### Post by Therion on 2008-01-25
Sart CCSM, enable the Place Windows plugin and then, under the General tab for that plug-in, use the drop down menu for "Placement Mode" and change the setting from "Smart" to "Centered".

---

### Post by andrewkk on 2008-01-25
> **Therion said:**
> Sart CCSM, enable the Place Windows plugin and then, under the General tab for that plug-in, use the drop down menu for "Placement Mode" and change the setting from "Smart" to "Centered".

Thank you for the suggestion. I don't want every window I open to pile up in the center though. Convenience of window management is -the- reason is use compiz, and this would be a step backwards I think.

Does everyone agree that this is probably a bug with the "Smart" placement algorithm?

---

