---
title: "Desktop Enviornements &amp; Driver question"
date: 2009-11-11
forum: Desktop Environments
---

### Post by deamon_knight on 2009-11-11
I know I can install Gnome, KDE & Xfce  desktops on the same machine, but If I want to compare them for performance will this work? I've heard that They will install each others services, but will that affect performance?

Also, I have installed Kubuntu 9.10, but while jockey prompts that there is am Nvidia driver I can install, choosing it does not do anything, it never shows activated. Am I doing something wrong? My video card is nVidia Corporation NV18 [GeForce4 MX 4000] (rev c1).

Thanks!

---

### Post by earthpigg on 2009-11-11
if you want to do a true comparison, you would need to use something besides GDM (ubuntu's default GNOME-centric login manager) as the login manager.

using GDM, gnome would have an advantage.

consider SLiM or xdm, which are not 'tailored' for any specific DE.

---

### Post by earthpigg on 2009-11-11
you would also need to ensure you are using GTK+ apps in the GTK+ desktop enviornments (gnome and xfce) and QT in KDE.

loading a QT app in GNOME means that gnome must first read a bunch of QT libraries. and vice versa for GTK+ in KDE.

how do you find out which is which?

search [here]("http://packages.ubuntu.com/karmic/gparted").

in that example, we have gparted. gparted depends on gksu. gksu depends on lib***gtk***. thus, we know that gparted is a gtk app because it relies on gtk to function.

gparted, thus, will almost certainly run faster and lighter in gnome or xfce than in kde -- but that isn't kde's fault *per se*.

---

### Post by deamon_knight on 2009-11-12
Ultimately could not not get used to Kubuntu, I installed Xubuntu and the drivers installed properly. -Thanks!

---

