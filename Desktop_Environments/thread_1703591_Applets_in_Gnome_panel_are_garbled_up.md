---
title: "Applets in Gnome panel are garbled up"
date: 2011-03-09
forum: Desktop Environments
---

### Post by peterdm on 2011-03-09
The clock applet and indicator applet in Gnome garble up from time to time. I have 2 Ubuntu installations at home and several others at work, some 32-bit and some 64-bit, all exhibiting the same issue occasionally. I think it's a bug in the Gnome panel. In the attached screenshot you can see an example of how the time in the clock applet is garbled up.

It's not always the clock that is affected, some other times it's the login name, the weather, or the shutdown button... Worst case, the shutdown button becomes totally invisible preventing me to log off (workaround: use the three-fingered salute).

It's a pretty annoying bug which I'd very much would like to see fixed some day.

Peter

---

### Post by Frogs Hair on 2011-03-09
You can restore to defaults , but this does not explain what is causing it and why many others are having the same problem.```
gconftool --recursive-unset /apps/panel && killall gnome-panel 
```

---

