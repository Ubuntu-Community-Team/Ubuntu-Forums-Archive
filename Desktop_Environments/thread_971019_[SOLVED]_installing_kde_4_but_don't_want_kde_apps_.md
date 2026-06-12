---
title: "[SOLVED] installing kde 4 but don't want kde apps all over the place"
date: 2008-11-04
forum: Desktop Environments
---

### Post by abh83 on 2008-11-04
I am currently running ubuntu 8.10.

I am planning on installing the kde4 desktop environment. However, is it possible to have the kde applications sorted into one place instead of having them mixed up along with my gnome apps?

And/Or is it possible to only install essential kde apps and not the 100s of useless apps that come along with it?


I think I remember reading a guide on this but I can't seem to find it.


Thx in advance!

---

### Post by benerivo on 2008-11-04
You can't keep them separate unless you edit your main menus after installation, but you can install just a base kde4 system with```
sudo apt-get install kde-core
```

---

### Post by abh83 on 2008-11-04
does the base kde4 system contain the eyecandy pre-installed with it? Supposedly the new kde4 desktop environment has integrated widgets with the its file manager... or something along these lines!

---

### Post by benerivo on 2008-11-04
It has the base set of plasmoids, which is what i think people refer to as the kde4 eye-candy. The theme/style/colour is almost identical to the full kubuntu-desktop installation.

---

### Post by abh83 on 2008-11-04
thx exactly what i was looking for!

---

### Post by nahian on 2008-11-06
after installing kde-4 if I dont like it how can I un-install it?

---

### Post by mfox on 2008-11-06
sudo apt-get remove kde-core

---

### Post by mfox on 2008-11-06
> **abh83 said:**
> does the base kde4 system contain the eyecandy pre-installed with it? Supposedly the new kde4 desktop environment has integrated widgets with the its file manager... or something along these lines!
If KDE4 is like KDE3, when you add just the kde-core to Ubuntu, openOffice application windows will be missing some icons.  I can't remember the name of the file, but there is an OO file with kde in its name that will fetch you those icons and make the windows look right.

---

