---
title: "kcm-gtk does absolutely nothing in 10.04"
date: 2010-07-19
forum: Desktop Environments
---

### Post by Zenith88 on 2010-07-19
It does not switch the decorations, the GTK apps in KDE are still butt ugly.
On top of that the changes it makes to the *gtkrc* files get replace with default every reboot.

Is there a reliable way to get GTK apps decorated in KDE under Lucid?

---

### Post by joeblurton on 2011-02-18
Does anyone know how to fix this? I have the same problem in Maverick and KDE 4.6. I've googled widely, but to no avail. Changes to the gtk theme settings are not only not persistent, they don't apply at all, and I'm stuck with the ugly Redmond theme.

---

### Post by joeblurton on 2011-02-18
Right:

```
sudo apt-get install gtk-theme-switch

gtk-theme-switch2
```

Change it there. For some reason KDE's GTK-switcher is buggered. Obviously this will GNOME look very odd.

---

