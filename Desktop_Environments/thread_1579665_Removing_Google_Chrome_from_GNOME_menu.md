---
title: "Removing Google Chrome from GNOME menu"
date: 2010-09-22
forum: Desktop Environments
---

### Post by szymm on 2010-09-22
Having uninstalled Google Chrome, I can't find a way to remove its GNOME menu entry. The icon is gone, there is no '.desktop' file, yet the entry remains and can't be removed through alacarte. Does anyone know what keeps it alive?

---

### Post by fancypiper on 2010-09-22
I don't know what you mean by "what keeps it alive?"

To remove it from the menu, right click on the menu, select edit and delete it's entry (and other unwanted items) from the menu.

---

### Post by szymm on 2010-09-22
It can't be done. I can neither disable nor delete this specific entry through the Menu Editor. If I try, it complains there is no 'google-chrome.desktop' file. It's kind of like the entry was deleted, but the menu doesn't know about it.

EDIT:
Okay, it can be solved by removing the entry before uninstallation. Thanks anyway. :)

---

### Post by VanillaMozilla on 2010-09-22
Sounds like a possible bug.  I'm wondering if you installed this from the Ubuntu repository, or from Google.  I think the installation methods are different, and maybe that accounts for the problem somehow.

---

### Post by szymm on 2010-09-22
I downloaded it from Google, and I'm pretty sure they messed something up. I've seen similar problems reported on their forums. I'm sticking to Chromium from the Ubuntu repository, it works fine.

---

### Post by VanillaMozilla on 2010-09-22
It could also be a Ubuntu problem.  Things can get installed in ways that apt or whatever doesn't really know about.  But you should be able to just delete the menu item.  There's even a button to delete menu items.

---

