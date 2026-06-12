---
title: "Login screen KDE not Gnome"
date: 2010-02-11
forum: Desktop Environments
---

### Post by rbrown3rd on 2010-02-11
My desktop running 9.10 and Gnome Desktop is performing flawlessly.  The only thing I see that I would change is that the splash screen and login shows KDE and the login screen manager in Gnome is grayed out.  This is a minor, cosmetic issue but I would like get it in harmony with my Gnome desktop and be able to use the built in login manager.

---

### Post by Zorael on 2010-02-12
To change the splash, do this in a terminal and, in the menu that pops up, select whatever rhymes with Ubuntu. Probably something like '**/usr/lib/usplash/usplash-theme-_ubuntu_.so**'. The second command could take a minute to complete if you have a lot of kernels installed.
```
$ sudo update-alternatives --config usplash-artwork.so
$ sudo update-initramfs -u -k all
```
To use the GNOME login manager (gdm) instead of the KDE one (kdm), do the following (again, in a terminal) and pick gdm.
```
$ sudo dpkg-reconfigure gdm
```
Also, unless you're mixing use of GNOME and KDE SC, you could just remove kdm, the Kubuntu usplash and whatever other bits you don't want encroaching on your GNOME sphere of existence.

---

### Post by rbrown3rd on 2010-02-12
That was easy enough.  Thanks very much.  Is there a way to customize that login screen now that it is setup for Ubuntu?

Oddly when I boot the system it shows the KDE pulsing bar for a second and then switches to the Ubuntu one.  After that the login screen is now the Ubuntu one but I would like to change the colors and the splash image if possible.

---

