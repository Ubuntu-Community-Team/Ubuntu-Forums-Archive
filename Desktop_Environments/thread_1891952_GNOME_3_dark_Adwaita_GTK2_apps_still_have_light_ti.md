---
title: "GNOME 3 dark Adwaita: GTK2 apps still have light titlebar"
date: 2011-12-06
forum: Desktop Environments
---

### Post by Vermind on 2011-12-06
Hi, I switched to the dark Adwaita theme and added a gtk-color-scheme line to gtk-2.0/gtkrc as per the instructions in [https://bbs.archlinux.org/viewtopic.php?pid=928975](https://bbs.archlinux.org/viewtopic.php?pid=928975) . However, my GNOME 2 windows (like Pidgin and Firefox) have a white titlebar (regular Adwaita style), while GNOME 3 windows are fine. The funny thing is that if I switch to regular, unmodified Adwaita, then restart gnome shell (Alt-F2 r) and then switch to the dark version, GNOME 2 windows also get a dark titlebar. However, it disappears on restart of gnome-shell, and I have to do the same trick again.
Any ideas on how to make this permanent?

Attached: a tar.gz that you can extract in the home folder to get the modified, Adwaita-dark theme.

---

### Post by Vermind on 2011-12-08
I have discovered a fix.
I copied the gtk-dark.css in the gtk-3.0 folder of my copy of Adwaita on top of the original gtk.css. I then set the dark theme option to false: ```
gedit $HOME/.config/gtk-3.0/settings.ini
```
Afterwards, the file looked like this:
```
[Settings]
gtk-application-prefer-dark-theme = false
```
I then restarted gnome-shell by typing gnome-shell --replace in a terminal.

So the conclusion is that prefer-dark-theme does not work properly, and that we still have a binary system of either dark theme or light theme, as it comes to the _titlebars_ of GNOME 2 windows.

---

