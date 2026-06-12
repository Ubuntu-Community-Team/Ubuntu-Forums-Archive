---
title: "KDE and GTK"
date: 2010-02-09
forum: Desktop Environments
---

### Post by TheNessus on 2010-02-09
Hey all.

A question:
When I had full Kubuntu installed, most gtk applications were rendered in qt. That was fine. However, Kubuntu is too bloated, so I now have kde-minimal, and I installed kcm-gtk which does a nice job, but gtk apps are still very ugly and not at all in qt. What else should I install to make it alright again?

thanks

---

### Post by 3Miro on 2010-02-09
Try System Settings -> Appearance and look for the GTK tab on the left. It should have options that you can play with.

---

### Post by lovinglinux on 2010-02-09
Install [gtk-qt-engine](apt:gtk-qt-engine) and then do [this](http://ubuntuforums.org/showpost.php?p=8107813&postcount=17).

I also use kde-minimal installation from a command-line only Ubuntu. It works great. I would also recommend kdeplasma-addons.

---

### Post by dE_logics on 2010-02-09
I got a feeling you gotta recompile the applications (by hand) with GTK support and -qt3 and 4

---

### Post by TheNessus on 2010-02-10
> **lovinglinux said:**
> Install [gtk-qt-engine](apt:gtk-qt-engine) and then do [this](http://ubuntuforums.org/showpost.php?p=8107813&postcount=17).

I also use kde-minimal installation from a command-line only Ubuntu. It works great. I would also recommend kdeplasma-addons.

worked :)

spanks

---

