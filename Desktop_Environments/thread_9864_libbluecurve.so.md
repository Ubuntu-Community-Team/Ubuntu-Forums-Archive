---
title: "libbluecurve.so"
date: 2005-01-02
forum: Desktop Environments
---

### Post by pavkonti on 2005-01-02
when i start mplayer and xmms i receive this warning

Gtk-WARNING **: Unable to locate loadable module in module_path: "libbluecurve.so"

where can I find this module libbluecurve.so

---

### Post by piedamaro on 2005-01-03
It means that it's searching for the bluecurve library i.e. the theme engine used in fedora as default one. Probably you have your gtk1 theme setted to bluecurve in a .gtkrc file in your home dir, maybe did you copy it from a fedora installation? Or are you sharing your home dir between fedora and ubuntu? (the latter is no good.)

---

### Post by pavkonti on 2005-01-04
i have installed only ubuntu + milk theme, made updates, installed xmms, compiled mplayer.

---

### Post by simplyw00x on 2006-08-03
Milk theme depends on bluecurve. You need to
sudo apt-get install gtk2-engines-clearlooks

---

