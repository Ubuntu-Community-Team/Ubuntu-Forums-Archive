---
title: "Making GTK apps take on your KDE style"
date: 2006-02-03
forum: Desktop Environments
---

### Post by Psimon on 2006-02-03
There's a package available called _gtk2-engines-gtk-qt_ which sets up an option in Kcontrol to have all your gtk apps look like your chosen KDE style, basically making all your applications look consistent. It does a great job but when I try to log back in, the system just hangs and I have to remove it.

I used to use it in Mandrake but this problem started when that distro was upgraded to 10.1, and it continues to be a problem in Kubuntu. I would love to get this working, so if you have any ideas please let me know.

---

### Post by xtacocorex on 2006-02-03
I have this installed and it works for me, in fact, I download the QtCurve style from KDE-Look yesterday and installed it since it covers both Qt and GTK apps. 

Before I installed QtCurve, my GTK apps didn't want to work with the KDE style, but after setting it properly with the GTK-Qt thing in KCM, it works (just takes a restart of the GTK apps)

It is odd that your system hangs, but are you sure it's directly related to the style?

If you got debugging info, I'd try sending it to the [program] developers, they would probably be able to tell you exactly what's going on.

---

### Post by superm1 on 2006-02-03
Its too bad there is no QT theme to go the other way around.  It would really be sweet if my QT apps could use all the clearlooks stuff.

---

### Post by Psimon on 2006-02-03
I tried again having installed QT Curve but I couldn't log in again. There was some output in the command line relating to 'xset' and it said something like 'Xdisplay is not set' and 'could not connect to DCOP sever'

I wonder if it could be because I have SCIM installed, as that has affected other apps in the past.

---

