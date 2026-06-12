---
title: "Sessions startup confusion"
date: 2008-05-15
forum: Desktop Environments
---

### Post by jamescoy on 2008-05-15
In the last couple of days, I've been (finally) able to get both Ubuntu Gnome and Kubuntu installed. Now, this may be just a cosmetic annoyance, but even if I start up in Gnome, when I restart, or shut down for that matter, the initial splash screen appears as Kubuntu. The booting continues and I end up (correctly) in whichever session I want to be in, but I can't figure out why the Kubuntu startup screen seems to override the regular Gnome Ubuntu startup screen.

Any ideas?

---

### Post by zenwalker on 2008-05-16
Probably, when u install Kde ad its libs, a Kdm might be installed over Gdm.

---

### Post by jamescoy on 2008-05-16
Is that normal or should KDE and GNOME run independently?

---

### Post by cyberdork33 on 2008-05-16
> **jamescoy said:**
> Is that normal or should KDE and GNOME run independently?
they are running independantly after the display manager loads them. kdm vs gdm is just the login window stuff which runs the appropriate commands to start the desktop environment that you want. If you really want to use something that is not gnome or kde, then you can use plain ol' xdm but it is not nearly as pretty.

---

### Post by frog_pilot on 2008-05-16
It's only the usplash, which is involved in this. It's independent from choosing the startup-manager (gdm or kdm) which you did during installation of kde desktop. on a certain point there will be a window asking you to selekt your default startup-manager.
The usplash only depends on the latest installation of a window-manager. If kde (kubuntu-desktop) was your final installation, then you will get the kubuntu usplash, also if you selected gdm as your default.

There are two ways to change this

To get back ubuntu usplash simply uninstall kubuntu-artwork-usplash. If you want to leave the kubuntu-desktop metapackage untouched execute ```
sudo update-alternatives --config usplash-artwork.so
``` to choose your preferred usplash and ```
sudo dpkg-reconfigure linux-image-$(uname -r)
``` to activate it.

---

