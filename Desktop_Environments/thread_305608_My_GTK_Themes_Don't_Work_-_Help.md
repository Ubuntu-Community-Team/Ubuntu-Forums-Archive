---
title: "My GTK Themes Don't Work - Help"
date: 2006-11-23
forum: Desktop Environments
---

### Post by super breadfish on 2006-11-23
Every GTK theme I install doesn't work! None of the buttons, scrollbars etc are themed properly. They are all themes that worked fine on Dapper, but since I reinstalled with Edgy none of them work. I've tried downloading them again from Gnome-look etc but with no luck.

The only thing I've noticed that looks out of place is this error that I get when I bring up Gnome Theme Manager from the terminal:

Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

but I have no idea what that means. Any ideas?

---

### Post by RAOF on 2006-11-23
The "engine" refers to the actual code used to draw the theme; GTK themes can use many engines, and you can install new engines.  It seems that the problem is that you don't have the "pixmap" engine installed, possibly because it is no longer installed by default.

You should be able to fix this by installing the **gtk2-engines-pixbuf** package.

---

### Post by super breadfish on 2006-11-24
That's fixed it all. Thanks!

---

### Post by Bashed on 2007-05-07
I had that already installed and was still getting the errors

```
chad@Secured:~$  sudo apt-get install gtk2-engines-pixbuf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gtk2-engines-pixbuf is already the newest version.
The following packages were automatically installed and are no longer required:
  libktnef1 libberylsettings0-gconf blt koffice-libs tcl8.4 tk8.4 libgpgme11
  koffice-data
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

What should I do?

---

