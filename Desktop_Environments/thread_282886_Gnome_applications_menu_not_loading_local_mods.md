---
title: "Gnome applications menu not loading local mods"
date: 2006-10-23
forum: Desktop Environments
---

### Post by arnaldo on 2006-10-23
I logged in today after a system crash; all seemed normal, except for the gnome Applications menu.  It looked like a vanilla, post installation one.

I checked the ~/.local directory, and all .directory and .desktop files were still there, uncorrupted.  Yet, none of these entries appeared in the menu.  The menu was fine, prior to the crash.

I tried to edit the menu with alacarte; I was able to create a new menu, however it stayed invisible (and appears in a different font in the alacarte menu).  There was no way of turning it into an active item, clicking the checkbox got no reaction.

I am using dapper, up-to-date, with several universe and multiverse packages thrown in.

---

### Post by ayllu on 2006-11-09
your file etc/xgd/applications.menu is corrupt and you need to replace it, if you have the original code is better i used a code from the internet, is not the original but its works, but i cudnt fix the system menu, because a need the preferences menu and the settings menu

---

