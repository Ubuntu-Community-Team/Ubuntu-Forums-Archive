---
title: "Wine, other menu, LXDE, Maverick and getting rid of menu entries"
date: 2011-04-06
forum: Desktop Environments
---

### Post by vanquishedangel on 2011-04-06
I see that this is a problem with LXDE and not having a menu for wine, or a menu editor. I have a pure LXDE install on Ubuntu maverick and i am loving it, but however there is that really annoying "other" menu and when i install in wine, and then uninstall the program in wine, the menu entry in the "other" menu stays.

I tried to purge wine and PlayonLinux, and i deleted the .wine and the .playonlinux files manually, that didn't work. I looked in the files that end with .desktop and there are no files for them there, so I can't just delete them, I also tried alacart but that botched my system and made it unbootable until i did autoremove. It seems that lxshortcut wont run from the terminal either. Really I don't need the other menu at all and would like it gone.

I have seen this issue on other forums with a long list of commands and alot of people cant follow them or claimed they never worked. I am hoping to get a good answer for me and all the others with this issue,
Thank you in advance

---

### Post by vanquishedangel on 2011-05-01
~/.local/share/applications/wine/

That is the path where the desktop files in the other menu were stored, just delete them and/or the folders this should take care of the issue.

---

