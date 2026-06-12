---
title: "Skype and KDE theme"
date: 2012-12-27
forum: Desktop Environments
---

### Post by perce on 2012-12-27
Skype 4.1 on kubuntu 12.04 seems not to follow the colour scheme dictated by the KDE theme; in particular the name of the selected contact is written in black over dark blue, making it unreadable. Is there any known solution to this issue?

---

### Post by dabl on 2012-12-27
I have a mostly all-defaults Kubuntu 12.04 installation, with Skype 4.1.0.20, and I don't see the issue as described.  Do you see it with the default "air" theme?  If not, what theme is showing the problem? What video hardware and driver are you using?

---

### Post by perce on 2012-12-28
I'm using the default theme. I have a Zenbook prime UX31A with intel Ivy Bridge graphic controller. I've installed the 64 bits version of Kubuntu and skype. Other people have the same problem, but google has found only solutions for Gnome.

---

### Post by dabl on 2012-12-28
I would suppose the problem is limited to certain GPU/driver combinations, the same or similar to what you have.  I don't have a system with that Intel Ivy Bridge controller, which is probably at the heart of the problem. I can't offer anything more than what google can find -- sorry.  :(

---

### Post by raelgc on 2013-03-16
perce,

Open Skype menu > Options > General, and under "Choose Style" select "GTK+" style.

Restart Skype.

---

### Post by petr_voinov on 2013-09-03
for me, only the following actions made stable effect:
1. install kde-config-gtk gtk2-engines-oxygen:i386
2. go to Sytem Settings -> Application Appearance
a. colors - select Oxygen Gold
b. GTK+ appearance - select oxygen-gtk

---

