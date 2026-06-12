---
title: "Windows-esque 3D windows scroller"
date: 2010-02-10
forum: Desktop Environments
---

### Post by Garnett on 2010-02-10
I've seen videos of a feature in the newer windows (XP's the last one I used) where a user can scroll through a 3D stack of open application windows (at least this is what it looks like)

I'm trying to pimp a new ubuntu machine to show it off to friends who have only ever used MS or Mac.

Is there anything like this feature for Linux?

---

### Post by ad_267 on 2010-02-10
Yes, install the compizconfig-settings-manager application and you can configure the compiz window manager to enable this effect. I can't remember what it's called but it should be one of the options for window switching. There are a lot of different effects you can enable and you might like something else better anyways, so just have a play around with the options in there.

Edit: I just installed it myself to check.
Make sure visual effects are enabled under System - Preferences - Appearance then after installing compizconfig-settings-manager go to System - Preferences - ComizConfig Settings Manager.
Go to Window Management and enable "Shift Switcher". Then under the options change the switcher mode to flip.

---

### Post by Garnett on 2010-02-10
Awesome - thanks a lot

---

### Post by Menthu_Rae on 2010-02-10
```
sudo apt-get install compiz fusion-icon compizconfig-settings-manager
```

System > Preferences > CompizConfig Setttings Manager

Then enable "Shift Switcher" or "Ring Switcher" and use WinKey (or "Start") on your keyboard + Tab. You can edit the effect settings by clicking on the effect name and adjusting the various sliders and drop down boxes.

---

