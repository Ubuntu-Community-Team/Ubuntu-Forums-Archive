---
title: "Reinstall GNOME and GTK+2, Please Help!"
date: 2007-05-04
forum: Desktop Environments
---

### Post by JordanII on 2007-05-04
I was trying to get a Mac Menu applet installed to GNOME and GNOME crashed. I powered down the comp and GNOME still didn't work. Fortinately I have Enlightenment installed on my computer so I can at least use that, but I want GNOME back. Also I think something got messed up with GTK. Does anyone know how to reinstall GNOME and GTK? Please Help, Thank you.

~Jordan

---

### Post by JordanII on 2007-05-05
Anyone?

---

### Post by ayoli on 2007-05-05
try this (in a terminal):
```
sudo apt-get clean && sudo apt-get update
sudo apt-get install libgtk2.0-0 libgtk2.0-bin libgtk2.0-common --reinstall
```

---

### Post by JordanII on 2007-05-05
I tried that and it did not work.

---

