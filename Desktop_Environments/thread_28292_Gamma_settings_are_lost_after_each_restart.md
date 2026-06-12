---
title: "Gamma settings are lost after each restart"
date: 2005-04-19
forum: Desktop Environments
---

### Post by SGC on 2005-04-19
Each time i restart my computer, i have to readjust this settings from:
control center > peripherals > display > monitor gamma 

although **save settings to XF86Config** are checked.

How can I make the gamma settings permanent?

---

### Post by heimo on 2005-04-19
Hmm... I'm not too familiar with this, but have you checked if there's any change in /etc/X11/xorg.conf after saving the settings? You could enter those values manually to Monitor section (man xorg.conf):
 ```
Gamma  red-gamma green-gamma blue-gamma
``` 

That should make them permanent.

---

### Post by SGC on 2005-04-20
Thanks heimo, it worked

---

