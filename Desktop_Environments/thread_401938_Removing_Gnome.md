---
title: "Removing Gnome"
date: 2007-04-05
forum: Desktop Environments
---

### Post by BlahBlahX on 2007-04-05
Hi guys. I am making a specialist version of Ubuntu, and I want to know how to remove all of Gnome except GDM.

Thanks.

---

### Post by ComplexNumber on 2007-04-05
impossible. it depends upon quite a few gnome libs.

---

### Post by koshatnik on 2007-04-05
I take it you ask because you want to create a bespoke ubuntu intall with a different desktop manager, but still want a gui for the login?

---

### Post by BlahBlahX on 2007-04-06
actually now i just want to remove the whole Gnome and install XFCE instead.

Can anybody help me out?

---

### Post by fibuntu on 2007-11-17
I think that you can just do: sudo aptitude install xubuntu-desktop, then log on the xfce and then sudo aptitude remove ubuntu-desktop. That would maybe work (although I've never tried)

---

### Post by LinuxSoundMan on 2007-11-17
you can install xfce via apt-get and it will give you an option at login weather u want to make it default or not. and from within xfce you can choose to disable all gnome bloat if im not mistaken. xfce is my environment of choice now and i must say it is really nice. doeas anyone know how to uninstall another window manager ive installed such as openbox and fluxbox. im not to sure about the uninstallation process as with fluxbox i also installed the "recomended" packages. any advice would be great. thanks

---

### Post by urukrama on 2007-11-17
GDM depends on a lot of gnome librararies, but you don't need to have the full Gnome desktop environment installed. An alternative login screen is [SLIM]("http://slim.berlios.de/").

---

