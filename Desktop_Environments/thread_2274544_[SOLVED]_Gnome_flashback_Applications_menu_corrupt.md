---
title: "[SOLVED] Gnome flashback Applications menu corrupt"
date: 2015-04-20
forum: Desktop Environments
---

### Post by xande on 2015-04-20
Ok, after hours of beating my head against the wall, I'm asking for help.  I'm running Ubuntu 14.04 LTS, using the Gnome flashback (Compiz) desktop (however, the same problem occurs with Gnome Flashback (Metacity)).  While trying to add a menu item via the Main Menu app, the app crashed.  Ever since then, clicking on the Applications menu does nothing (it gives the "depressed" graphical change, but no menu appears).  Right-clicking on "Applications" shows the "Edit Menus" option, but clicking on it causes a "Main Menu" window to flash into existence and immediately disappear.  Starting "Main Menu" via Gnome-Do does the same.  The "Places" menu and other GNOME panels work perfectly.  Starting applications via Gnome-Do works fine.

I've tried logging out and back in, rebooting, and various methods for resetting Gnome panels that google turned up, but so far, nothing has helped.
(Resetting methods tried were the following, with "killall gnome-panel" and/or logout and back in after each.)
```
gconftool-2 --recursive-unset /apps/panel
dconf reset -f /org/gnome/gnome-panel/
mv ~/.config/menus/applications.menu ~/.config/menus/applications.menu.bak && mv ~/.config/menus/settings.menu ~/.config/menus/settings.menu.bak

```

Any suggestions?

EDIT: Figured out a solution.  If anyone else has this problem, what worked for me is this:
```

 mv .config/menus/gnome-flashback-applications.menu .config/menus/gnome-flashback-applications.menu.bak

```
(Of course, deleting the applications.menu file would work as well, but the above saves a copy, just in case.)

---

