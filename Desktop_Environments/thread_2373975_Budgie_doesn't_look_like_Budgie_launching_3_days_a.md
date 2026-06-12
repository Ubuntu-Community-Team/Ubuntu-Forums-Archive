---
title: "Budgie doesn't look like Budgie launching 3 days after install"
date: 2017-10-11
forum: Desktop Environments
---

### Post by qviss on 2017-10-11
Hi,
I'm pretty new to the Linux world and had some issues getting any Linux distro to install, but I managed to get a few of them up and running and I liked Ubuntu Budgie the best. I lauched the OS and everything seemed fine the first 2 days. Today (3 days after installing), I launch my computer and Budgie doesn't look anything like it did when I installed it. The menu launcher has, I guess, a GNOME foot logo and my wallpaper just disappeared (changed to a solid blue color). My Terminix also came up with an error (config error) that I managed to fix but it all sounds so fishy. Does anyone have any idea on what might be causing this? (and yeah, i restarted my computer multiple times, it's always the same)

---

### Post by Frogs Hair on 2017-10-11
Budgie has made major changes to the desktop including moving settings from the raven panel to a separate settings application. The gnome foot will appear for icon sets designed for Gnome and not Budgie.

Image from  Budgie 10.4.

---

### Post by davidmohammed on 2017-10-12
you have uninstalled two critical packages - probably when uninstalling something else.

To fix

    sudo apt install --reinstall ubuntu-budgie-desktop budgie-desktop-environment

Then reboot.

---

