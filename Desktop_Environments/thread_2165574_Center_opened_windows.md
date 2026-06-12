---
title: "Center opened windows"
date: 2013-08-05
forum: Desktop Environments
---

### Post by mayagrafix on 2013-08-05
When I start an App, such as Firefox, Thunderbird, Nautilus, etc. the window-app appears at the top left corner of my PC screen, which is of the wide variety, up next to the Dash Home button in the Launcher.

I then proceed to drag said window to middle of the screen for my viewing comfort. This gets old very quickly, as u can imagine, so my question is: How can I change the default distance at which the window opens? so that it opens in the center of the screen instead of the top left corner?

Thanks for your answer :KS

---

### Post by Frogs Hair on 2013-08-05
If the compiz-configuration-settings-manager installed there are some of settings under window management that may help . I think "Place Windows" is the plug-in you may be looking for. I also have the compiz-plugins package installed and don't remember if place windows is a default plugin or an additional one.

---

### Post by stinkeye on 2013-08-05
> **mayagrafix said:**
> When I start an App, such as Firefox, Thunderbird, Nautilus, etc. the window-app appears at the top left corner of my PC screen, which is of the wide variety, up next to the Dash Home button in the Launcher.

I then proceed to drag said window to middle of the screen for my viewing comfort. This gets old very quickly, as u can imagine, so my question is: How can I change the default distance at which the window opens? so that it opens in the center of the screen instead of the top left corner?

Thanks for your answer :KS
Use ccsm to set the window placement mode. 
May need to install...
```
sudo apt-get install compizconfig-settings-manager
```
ccsm > window management > place windows

---

### Post by mayagrafix on 2013-08-05
Thanks!!

---

