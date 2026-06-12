---
title: "look of qt apps on gnome"
date: 2008-06-28
forum: Desktop Environments
---

### Post by usien on 2008-06-28
how to make qt apps look like gtk apps on gnome?

---

### Post by Can+~ on 2008-06-28
QT3 or QT4?

You can install the control centers for each one:
```
sudo apt-get install qt3-qtconfig qt4-qtconfig
```
(Leave the one you want).

Once installed, run anyone:
```
qtconfig-qt3
qtconfig-qt4
```

You can install themes, and anything you want.

---

### Post by usien on 2008-06-29
Thankyou. I installed that package and it is working but i have not found an option that makes qt  apps look like gtk, how to do that?

---

### Post by p_quarles on 2008-06-29
You can't, not yet anyway. Development versions of Qt 4 have such a plugin now, but the versions currently in wide usage do not. 

In the meantime, the QtCurve engine was designed to make Qt apps look more or less similar to GTK apps. That's the closest you're going to get for a while.

---

### Post by gatewayasteroid on 2008-06-29
> **usien said:**
> how to make qt apps look like gtk apps on gnome?

To make KDE applications look well integrated in my XFCE desktop, I use the Clearlooks theme for GTK, and Klearlooks for KDE (via kcontrol, or qtconfig-qt3).

Both themes can be found in the repositories.

---

