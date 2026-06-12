---
title: "How to change GDM background in _minimal_ installation with LXDE?"
date: 2014-02-21
forum: Desktop Environments
---

### Post by Artif on 2014-02-21
I have _minimal_ Ubuntu 12.04 install, LXDE desktop, GDM. Some parts of Gnome are installed, but not all, only some parts.

I have solid blue color background at GDM login screen. How can I place a picture here?

I searched for how to change GDM background, but all the methods are not applicable in the case. All of them are referencing on unexistent big configuration files, unexisten directories and so on. Some of the methods need to be installed tons of packages, but I want to keep LXDE/GDM system. I'm not shure that 70+ packages will not significantly change base "mechanics" and I'll not loose light weight infrastructure.

I'm shure there is a place where I can simply write down path do desired file, or where I can simply place renamed desired file. Is there such a place nowdays? As it was several years ago.

---

### Post by ibjsb4 on 2014-02-21
Two places that background could come from.

#1 Your default theme

#2 /usr/share/backgrounds

You can also change backgrounds using either gconf or dconf editor.

---

