---
title: "Reconfiguring Xubuntu 14.04 to Distribution Defaults"
date: 2014-05-25
forum: Desktop Environments
---

### Post by sudo san on 2014-05-25
Hi, I have recently upgraded my Xubutnu 13.10 install to Xubuntu 14.04. Now, the upgrade went fine but I did a fresh install of Xubuntu 14.04 on another machine. I quite like the set-up of the default configuration of Xubuntu 14.04. I was wondering if there is a way to revert to the default configuration. I was thinking that there may be a method through ```
dpkg-reconfigure
``` but there are many packages related to xfce4.

Does anyone have any suggestions of which packages to reconfigure? I don't want to just try it and end up ruining any config files that would render my install unusable.

Thanks :)

---

### Post by Toz on 2014-05-25
The easiest way would be to delete (or move if you want to save the data for future reference) the **~/.config/xfce4** and **~/.cache/sessions** directories. You should do this while not logged in (from Ctrl+Alt+F1). Then the next time that you login graphically (Ctrl+Alt+F7), those directories will be re-created with the distro defaults.

---

### Post by sudo san on 2014-05-25
Thanks! Deleting these files did cause fresh ones to be generated.

Marked as solved for others and remembered for future upgrades :D

---

