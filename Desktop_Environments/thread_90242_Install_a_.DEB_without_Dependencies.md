---
title: "Install a .DEB without Dependencies???"
date: 2005-11-14
forum: Desktop Environments
---

### Post by ace2005 on 2005-11-14
As far as i can remember i have had RPM based distros and it feels strange asking how to install a deb without dependencies but here i go.

How do i install a .DEB without Dependencies???

---

### Post by sigma2805 on 2005-11-14
so you mean that you don't want to install any dependancies only the file?

if so the following command should work....i think 

sudo dpkg --force-depends -i <filename.deb>

---

### Post by ace2005 on 2005-11-14
Well since you ask i'm trying to install kdelibs4-dev for KDE 3.5 RC1, which i need since i'm trying to compile KBFX and the SuSE window border and they are refusing to compile without the dev packages, but the thing is they depend on libarts1-dev which has to also be from KDE 3.5 RC1 which in turn want to install Arts from KDE 3.5 RC1 which breaks Juk and it keeps crashing every time it starts. So i'm going to keep Arts from KDE 3.5 Beta 1 installed and force install the dev packages of KDE from 3.5 RC1 and the dev packages of arts from KDE 3.5 Beta1.

And it works like a charm, Thanks :)

---

