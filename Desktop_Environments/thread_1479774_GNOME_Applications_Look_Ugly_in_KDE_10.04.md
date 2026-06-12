---
title: "GNOME Applications Look Ugly in KDE 10.04"
date: 2010-05-11
forum: Desktop Environments
---

### Post by iampriteshdesai on 2010-05-11
I installed KDE desktop in Ubuntu 10.04 now all GTK apps look ugly when I log into KDE.
I tried installing gtk-qt-engine-kde4, but I get this:
pritesh@ubuntu:~$ sudo apt-get install gtk-qt-engine-kde4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gtk-qt-engine-kde4


WHat should I do?

---

### Post by Mrvs on 2010-07-02
gtk-qt-engine is now replaced by kmc-gtk, which doesn't work anyway, at least for me.

---

### Post by Zorael on 2010-07-02
**kcm-gtk**.

You'll also need to make sure the **.gtkrc-2.0-kde4** file it creates is properly exported. It should be saved as soon as you apply settings in the GTK+ Appearance section. The file exporting it may or may not do this if you don't have **kubuntu-default-settings** installed.

Saved as **~/.kde/env/gtk2-engines-qtcurve.rc.sh**;
```
#!/bin/bash

# Make sure our customised gtkrc file is loaded.
export GTK2_RC_FILES=$HOME/.gtkrc-2.0-kde4
```

---

### Post by Mrvs on 2010-07-02
Installing kubuntu-default-settings worked like a charm. Thanx Zorael.

---

### Post by hazica on 2010-07-02
Not meaning to butt in or anything, but there's another solution for a slightly better integration of Gnome apps in KDE: [http://kde-look.org/content/show.php?content=103741]("http://kde-look.org/content/show.php?content=103741")

It works with KDE SC 4.4 and it comes in two flavours: standard and flat (without the gradient)

You'll find the installation instructions in the download package.

---

