---
title: "Alacarte Dependencies"
date: 2012-05-21
forum: Desktop Environments
---

### Post by Frogs Hair on 2012-05-21
After removing Gnome-session-fallback alacarte no longer worked in Unity or the Gnome shell. This was discovered when attempting to change an icon from the main menu. 

Some research suggested that it was a bug, but when reading the bug report I found that alacarte is dependent on the Gnome panel. Is there a way to remove Gnome Classic and keep alacarte working ? I was happy to have this unused DE off the login menu , but it seems I need it to use alacarte.

---

### Post by zombifier25 on 2012-05-21
I did an apt-cache show alacarte, and it says that alacarte *recommends* gnome-panel, not dependent on it. Try apt-get'ing it with the --no-install-recommends flag.
Sorry, can't check if it works because I don't want to remove gnome-panel at the moment.

---

### Post by diesch on 2012-05-21
Alacarte uses *gnome-desktop-item-edit  *from the package *gnome-panel* to edit menu item properties. Without that package the "*Properties*" button doesn't  work.

*gnome-panel*  only reccommends *gnome-fallback-session* so you can remove that while keeping *gnome-panel* . But you should explicitly install *gnome-panel *so it doesn't get remove by autoremove[I].
[/I]

---

### Post by Frogs Hair on 2012-05-21
Thank you both for the replies I will try what zombifier25 suggested and do some additional searching it that fails.

---

### Post by Frogs Hair on 2012-05-21
I checked the dependency list, removed gnome-session-fallback (GSF) again and alacarte is working fine after rebooting which I had done many times after removing GSF the first time. I plan to find out why the Gnome Panel is recommended though.

---

