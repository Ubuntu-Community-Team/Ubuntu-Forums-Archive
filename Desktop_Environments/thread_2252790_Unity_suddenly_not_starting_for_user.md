---
title: "Unity suddenly not starting for user"
date: 2014-11-14
forum: Desktop Environments
---

### Post by r0t on 2014-11-14
All of a sudden, Unity does not start when logging in. I have only a desktop, no dash, no panels, nothing else. The problem is limited to one user account.

Doing ctrl-alt-F1, and running [FONT=Courier New]export DISPLAY=:0[/FONT] and [FONT=Courier New]compiz --replace[/FONT] does restore dash (but not panel) for the current session only.

This is what I tried so far, without any success:

 * removing [FONT=Courier New]./config/compiz-1[/FONT], reboot

 * running [FONT=Courier New]ccsm[/FONT] and make sure all required plugins are enabled

 * [FONT=Courier New]apt-get install --reinstall ubuntu-desktop[/FONT], as well as [FONT=Courier New]unity[/FONT]

When trying

     [FONT=Courier New]export DISPLAY=:0
     dconf reset -f /org/compiz/
     setsid unity[/FONT]

I get the following error:

    [FONT=Courier New][drm:intel_lvds_enable] *ERROR* timed out waiting for panel to power on
[/FONT]
Any ideas about what to try next?

---

### Post by CantankRus on 2014-11-14
Can you boot to a previous kernel?

---

### Post by r0t on 2014-11-17
The problem, it seems was with [FONT=Courier New]lightdm[/FONT]. I still don't know what happened, but purging and reinstalling [FONT=Courier New]lightdm[/FONT] magically helped!

---

