---
title: "screensaver works first time only"
date: 2010-04-08
forum: Desktop Environments
---

### Post by mfearby on 2010-04-08
I'm running 9.10 64-bit and the screen saver will activate the first time after boot, but thereafter all I get is a black screen until the power management kicks in. Why is this?

---

### Post by mfearby on 2010-04-10
While I'm at it, is there a file somewhere that I can edit to specify a custom value for System > Preferences > Power Management > "Put display to sleep when inactive for"? 10 minutes is too quick and 30 minutes is too long. I have no idea why we can't just have a slider in there so we can have what we want. Well, I kinda do have an idea, and it's GNOME's "we know best" policy, but surely there's a way to override it?

---

### Post by mfearby on 2010-04-17
I opened gconf-editor and found /apps/gnome-screensaver and edited both idle_delay (to 10) and power_management_delay (to 20) but X is still ignoring the setting (by simply timing things after reboot, not by checking the GUI applet). Isn't this where the settings would be obtained by X?

---

