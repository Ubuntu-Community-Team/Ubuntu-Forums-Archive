---
title: "unable to access main menu"
date: 2008-11-08
forum: Desktop Environments
---

### Post by AntiHeroJoe on 2008-11-08
I've just gone through the upgrade process and am working my way through the issues now (have never had a clean ubuntu upgrade, sadly). I'm trying to edit the main menu, and if I go System > Preferences > Main Menu, nothing happens at all.

If I run alacarte from the terminal, I get the following output:

```
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 22, in <module>
    from Alacarte.MainWindow import MainWindow
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 19, in <module>
    import gtk, gtk.glade, gmenu, gobject, gnomevfs, gnome.ui
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
ImportError: /usr/lib/libgtk-x11-2.0.so.0: undefined symbol: pango_layout_set_height
```

What do I do, haha? Please help!

---

### Post by AntiHeroJoe on 2008-11-08
I've tried re-installing alacarte to no avail. I haven't turned up anything while searching google. halp!

---

### Post by AntiHeroJoe on 2008-11-09
please see [http://ubuntuforums.org/showthread.php?t=975887&page=4](http://ubuntuforums.org/showthread.php?t=975887&page=4) for solution

---

