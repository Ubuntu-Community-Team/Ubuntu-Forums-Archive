---
title: "right-click menu itmes in order to uninstall"
date: 2007-05-08
forum: Desktop Environments
---

### Post by pagingmrherman on 2007-05-08
Hi I was wondering if anyone knows if there's an easy way to modify the right-click menu that shows up when you're in the ubuntu main menu.  I want to make a script so that when you right click on an icon, it shows an 'uninstall' option.  The script would check the name of the file that the launcher runs, then do a

wajig whichpkg <filename> to get the package name, then do a 
wajig purge <package name> to uninstall it.

It would be an easy way to clean up stuff you've installed but don't want anymore.

---

### Post by blackened on 2007-05-08
I might just be naive, but I think those menus are hardcoded and would require custom recompilation of gnome itself to change.

---

