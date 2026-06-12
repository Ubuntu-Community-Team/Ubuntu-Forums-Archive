---
title: "WHOOPS broke beryl."
date: 2007-07-06
forum: Desktop Effects &amp; Customization
---

### Post by Tavorisch on 2007-07-06
Screwing around trying to get beryl to run at login! succeed! everything works perfectly!
except 1 thing. my embedded terminal on the desktop has a window around it! stupid
emerald themes throwing their red wobbly window decor on my sweet looking embedded terminal.
So i play with the settings off the drop menu on the emerald in the upper right of the menu bar., and i force AIGLX because im using ati right.. now beryl crashes, and it saved that setting and crashes everytime... so i have completely removed beryl 2 times from synaptic and via terminal too, sudo apt-get remove beryl beryl-core beryl-manager, emerald-themes beryl_settings_manager and resinstalled and it seems like that setting is stuck because now it crashes every time!! If i could just have enough time to pull that drop down from the emerald once beryl runs. How else would i change it to auto instead of FORCE AIGLX. or where is it saving that setting!?!? any help much appreciated guys.

---

### Post by Waappu on 2007-07-06
Hi

That setting is stored in file ```
.beryl-managerrc
```
You can delete that file by typing in terminal```
rm ~/.beryl-managerrc
```
When you next time start beryl-manager it will generate new file with default settings

---

