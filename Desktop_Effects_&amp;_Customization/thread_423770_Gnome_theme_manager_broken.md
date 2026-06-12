---
title: "Gnome theme manager broken"
date: 2007-04-26
forum: Desktop Effects &amp; Customization
---

### Post by DrQuincy on 2007-04-26
I was running KDE with the Baghira theme.  I installed ubuntu-desktop and ran Gnome as my default.  I uninstalled Baghira and now it's using some ugly grey theme.  When I go to Settings > Themes it crashes.

If I do gnome-theme-manager from the shell I get:

gnome-theme-manager: symbol lookup error: /usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so: undefined symbol: setColors

Any ideas how to fix it?

---

### Post by DrQuincy on 2007-04-27
If I sudo gnome-theme-manager from the shell I get this in a dialog box:

Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager

Any ideas?  Looks like something from KDE is interfering.

---

### Post by Magni on 2007-05-04
hi,

do you have fixed it?

---

