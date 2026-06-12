---
title: "Disable nautilus during GNOME startup for 8.10"
date: 2008-11-24
forum: Desktop Environments
---

### Post by jedrik on 2008-11-24
Under 8.04 and earlier it was possible to disable nautilus at startup
by using gnome-session-properties.  Under 8.10, nautilus is NOT listed there.  It is NOT included in ~/.gnome2/session.


Is there some way to control ALL the programs that are activated at startup?

---

### Post by thierryg on 2008-11-26
Solution to the nautilus problem: ask nautilus not to show the desktop.

Start gconf-editor in a Terminal.

Choose apps>nautilus>preferences>show-desktop and deselect it.

But I'm still searching for the 8.04 session panel which used to show the running programs...

---

### Post by DJ_Peng on 2008-11-27
Are you thinking of the list of apps to run at startup (*System > Preferences > Sessions*) or the list of apps currently running (*System > Administration > System Monitor*)?

---

