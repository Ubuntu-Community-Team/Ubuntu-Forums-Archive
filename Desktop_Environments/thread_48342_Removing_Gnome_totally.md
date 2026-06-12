---
title: "Removing Gnome totally"
date: 2005-07-12
forum: Desktop Environments
---

### Post by martinjh99 on 2005-07-12
I have installed Ubuntu and KDE I now want to remove Gnome totally.

What package can I remove to make apt remove the rest of Gnome?

I tried removing ubuntu-desktop with aptitude but it only removed ubuntu-desktop...

---

### Post by mp3guy on 2005-07-12
i don't know why'd you want to, but shutdown x (ctrl+alt+backspace)

sudo apt-get remove gdm

---

### Post by brent on 2005-07-12
ubuntu-desktop is a dummy package. It's nothing itself but it depends on other packages that make up the GNOME. So it installs GNOME, but it doesn't work the other way.

There's two things you could do. Either go through the packages and remove the gnome related ones, or format and install Kubuntu.

---

