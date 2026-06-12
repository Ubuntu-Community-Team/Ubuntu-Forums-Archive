---
title: "Changing Gdm theme"
date: 2009-04-15
forum: Desktop Environments
---

### Post by Swatfoot on 2009-04-15
Im want to change my gdm theme but get this error how do i change it and or get it running. Thanks for any help.

"GDM (GNOME Display Manager) is not running

You might be using a different display manager, such as KDM (KDE Display Manager), CDE login (dtlogin), or xdm. If you wish to use this feature, then your system will need to be configured to use GDM instead."

---

### Post by gjoellee on 2009-04-15
Try this command:
```
sudo /etc/init.d/gdm start     
```(Just copy and paste the command above (and you might need to hit the enter button) into the terminal. You can open the terminal form the menu.

Then try to install the GDM theme again.

---

