---
title: "Gnome-theme-manager missing in kubuntu"
date: 2007-10-28
forum: Desktop Environments
---

### Post by BruceBerry on 2007-10-28
Hello,

i just upgraded to 7.10 with a fresh install and being a kde user i installed kubuntu. I am now willing to give a try to GNOME so i installed the meta-package ubuntu-desktop and ran GNOME. Everything seemed fine... but i'm missing gnome-theme-manager!
Gnome-art (which i suppose is a program to automate retrieval of themes, icons and wallpapers from gnome-art.org, just like kde has a similar thing for kde-look.org) fetches the list and downloads art correctly, but then fails to install it because gnome-theme-manager is missing:
```
sh: gnome-theme-manager: not found
```

Am i missing the package which contains gnome-theme-manager?
I thought ubuntu and kubuntu were just different in terms of default packages installed...

Thank you

---

### Post by Kizlum on 2007-10-28
It seems that gnome-theme-manager is not longer used and gnome-appearance-properties replaces it.

---

### Post by BruceBerry on 2007-10-28
so this is a bug in gnome-art?

---

### Post by Zeroedout on 2007-11-03
you could always try a symbolic link.  if memory serves, sudo ln -s /usr/bin/gnome-appearance-properties /usr/bin/gnome-theme-manager

---

