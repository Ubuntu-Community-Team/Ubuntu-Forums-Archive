---
title: "GDM or X11 Crashing Immediately After Login"
date: 2009-01-06
forum: Desktop Environments
---

### Post by johnnybg00de on 2009-01-06
Hi,

Whenever I attempt to login to my Ubuntu 8.04 from the GUI login prompt GDM or X11 fails to start. My uname and pass are accepted by the login screen, however the orange transition screen immediately turns grey and I am sent back to the login screen.

By hitting Ctrl-Alt-F1 I am able to log directly into bash. In an attempt to reset my gdm settings I have already run the following command:

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

I have also attempted to remove and reinstall my gdm and ubuntu-desktop packages via apt-get.

I am at a loss for what could be causing this problem. Any help is much appreciated.

---

