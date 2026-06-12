---
title: "ubuntu-desktop"
date: 2005-06-10
forum: Desktop Environments
---

### Post by gwon on 2005-06-10
To switch from kubuntu to hoary standard, am I correct in assuming that all I have to do is update my sources.list to the hoary sources and:

apt-get remove kubuntu-desktop
apt-get install ubuntu-desktop

I think that's correct..

Thanks  :)

---

### Post by shakin on 2005-06-10
[QUOTE=gwon]To switch from kubuntu to hoary standard, am I correct in assuming that all I have to do is update my sources.list to the hoary sources and:

apt-get remove kubuntu-desktop
apt-get install ubuntu-desktop

I think that's correct..

Thanks  :)[/QUOTE]

Removing kubuntu-desktop will not remove KDE or any of its libraries. It's a meta-package that points to Kubuntu packages to install them, but the reference doesn't work in reverse. Even while using Gnome you may wish to keep the libs so you can run QT (KDE) apps while in Gnome. I'm sure you don't need all of KDE to do this, but I don't know exactly which packages are safe to remove.

Installing ubuntu-desktop will get you Gnome and gdm just like with Hoary standard.

---

### Post by gwon on 2005-06-10
[QUOTE=shakin]Removing kubuntu-desktop will not remove KDE or any of its libraries. It's a meta-package that points to Kubuntu packages to install them, but the reference doesn't work in reverse. Even while using Gnome you may wish to keep the libs so you can run QT (KDE) apps while in Gnome. I'm sure you don't need all of KDE to do this, but I don't know exactly which packages are safe to remove.

Installing ubuntu-desktop will get you Gnome and gdm just like with Hoary standard.[/QUOTE]
 Ok, brilliant. I don't really need to get rid of KDE anyway, I just thought it may have caused some conflicts.

Thanks.

---

### Post by az on 2005-06-10
What is great is that if one package causes conflicts, it removes the offending packages, if that is possible.  If it is not possible, apt will refuse to proceed.

---

### Post by gwon on 2005-06-10
[QUOTE=azz]What is great is that if one package causes conflicts, it removes the offending packages, if that is possible.  If it is not possible, apt will refuse to proceed.[/QUOTE]
 I've ran into a slight problem that hopefully someone can help with..

Everything seems to have gone fine, except the desktop icons (Home, System, Wastebin), all other icons are fine. It happens no matter which icon theme I choose.

I tried to install the icons package via apt-get but was told that the current package is up-to-date. Any help or ideas would be appreciated.

---

### Post by sbassett on 2005-06-10
Did this happen to be after switching to KDE and then back to GNOME? If so, this has happened to me as well. Please verify that you have GNOME not to show icons on the desktop and then remove the remaining icons that are on the desktop.

Please see this link for hiding/showing icons on the desktop:
[http://ubuntuguide.org/#showdesktopicons](http://ubuntuguide.org/#showdesktopicons)

---

### Post by Joeb on 2005-06-10
[QUOTE=gwon]Ok, brilliant. I don't really need to get rid of KDE anyway, I just thought it may have caused some conflicts.

Thanks.[/QUOTE]

However, if you did want to remove KDE, you would just tell apt-get to remove kdelibs and it and every kde application on your system would be removed as they all depend on it.

Then if you wanted just a specific app or two (maybe K3b), just install it and only the libs that are required would be installed back.

---

### Post by gwon on 2005-06-10
[QUOTE=sbassett]Please see this link for hiding/showing icons on the desktop:
[http://ubuntuguide.org/#showdesktopicons](http://ubuntuguide.org/#showdesktopicons)[/QUOTE]

You sir, are a saviour :)

[QUOTE=Joeb]However, if you did want to remove KDE, you would just tell apt-get to remove kdelibs and it and every kde application on your system would be removed as they all depend on it.

Then if you wanted just a specific app or two (maybe K3b), just install it and only the libs that are required would be installed back.[/QUOTE]

Thanks for that, but I actually managed that myself when I was looking through synaptic :) Thanks though.

**Thank you to everyone who helped me.**

---

