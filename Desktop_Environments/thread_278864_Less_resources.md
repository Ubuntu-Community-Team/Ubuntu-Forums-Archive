---
title: "Less resources?"
date: 2006-10-17
forum: Desktop Environments
---

### Post by r6mile on 2006-10-17
I know XFCE consumes very few resources, but what desktop environment consumes less resources: KDE or Gnome?

---

### Post by aysiu on 2006-10-17
Depends on whom you ask and what versions of KDE or Gnome you're running.

You can have KDE and Gnome both stripped to the bone so that neither is running many services at all.

Of course, you'll get many people saying "Gnome consumes fewer resources" and others saying "KDE consumes fewer resources."

Just try them both out.

I would advise installing *gnome-core* and *kde-core*, though, instead of *ubuntu-desktop* and *kubuntu-desktop*.

Paste these commands in the terminal, log out, then pick your session from the login screen options: ```
sudo aptitude update
sudo aptitude install gnome-core
sudo aptitude install kde-core
``` Of course, if resources are a real concern to you--and you're not just asking to start a flamewar--then you're probably better off with a window manager.

I've found IceWM to be extremely friendly to the new window manager user. You can also investigate Fluxbox, OpenBox, Windowmaker, and Enlightenment. Those get highly recommend in these forums.

---

