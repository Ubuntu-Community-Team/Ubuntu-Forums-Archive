---
title: "Switching to KDE, Xfce"
date: 2006-02-05
forum: Desktop Environments
---

### Post by Byte on 2006-02-05
How can I switch to KDE, and Xfce and back to Gnome when i'm finished? What are the risks/any pointers etc.

Thaks in advance,
 -- /usr/bin/byte

---

### Post by bartbes on 2006-02-05
To download: ```

KDE:
sudo apt-get install kubuntu-desktop

XFCE:

sudo apt-get install xubuntu-dektop

```

and to run them go in GDM to sessions and choose KDE or XFCE

to remove: ```

KDE:
sudo apt-get remove kubuntu-desktop

XFCE:
sudo apt-get remove xubuntu-desktop

```
but I won't recommend uninstalling after use

---

### Post by Byte on 2006-02-05
Thanks, but how do I access/use GDM and you say not to uinstall the new DEs - why not?

 -- /usr/bin/byte

---

### Post by taurus on 2006-02-05
After your system finishes booting, you will present a login screen.  Go into Session and click on whichever window manager that you want to use for that session...

---

