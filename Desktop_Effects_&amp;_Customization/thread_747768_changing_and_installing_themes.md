---
title: "changing and installing themes"
date: 2008-04-06
forum: Desktop Effects &amp; Customization
---

### Post by Mottq on 2008-04-06
I was trying to add some new themse that i got from GNOME-Look, and found out that my preference  menu hangs up on me (It is very difficult to change anything and trying to install thems is next to impossible). I am using Ubuntu 7.10 with Compiz-Fuzion, 1 Gig memory.

---

### Post by jay019 on 2008-04-07
Just tried this and seems to work...

Go to your .themes directory. Rename the folder containing the offending theme.
Copy a theme know to work (eg /usr/share/themes/human), renaming that folder to the offending theme name.

Restart desktop.


EDIT: Actually just re-read your post and if the Preference menu is hangin then your problem may not be solved with a theme change. Sorry I cant help in that regard.

---

### Post by FuturePilot on 2008-04-07
Try this
```
sudo apt-get remove --purge gtk-qt-engine
```
The theme manager doesn't seem to like the gtk-qt-engine
That will uninstall the engine.

---

### Post by Mottq on 2008-04-07
I've got it working! Thank you so much for your help.

---

