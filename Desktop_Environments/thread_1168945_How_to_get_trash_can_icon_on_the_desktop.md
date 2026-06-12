---
title: "How to get trash can icon on the desktop?"
date: 2009-05-24
forum: Desktop Environments
---

### Post by klopus on 2009-05-24
I mean good old trash icon on the desktop without resorting to screenlets or panel and dock widgets.My wife's netbook has a limited screen estate and so I keep both panel and AWN on auto-hide. This makes it very inconvenient to drag files to the trash icon - technique my wife insists on doing being a non-tech Windows user and all that. I have to respect her wishes :p

I tried to create a desktop shortcut from Nautilus but the damn thing doesn't have anything like that when you right click on the Trash icon. Btw, things like this is what drives Windows users away from Linux. As a last resort I tried to make a symbolic link from bash but can't figure out where's trash dir/file in Gnome.

It could very well something really simple that I miss so please bear with silly me :) Any help?

---

### Post by Sarai the Geek on 2009-05-24
Install Ubuntu Tweak:

```
sudo apt-get install ubuntu-tweak
```Run it (it's in system tools) and click the "desktop" tab on the side- it gives you an option to enable a trash can icon on the desktop!

By the way, I agree, it is sort of an annoyance that a lot of these simple things require Ubuntu Tweak. UT should probably be installed by default in future versions.

---

### Post by ckonestroh on 2009-05-24
No, don't load tweaks for this

alt+f2

Type gconf-editor > apps > nautilus> desktop

You can add trash can or home folder or Network icon or computer icon...

if you use compiz you must go into compiz to show trash can


later...

---

### Post by xXeHPiCXx on 2009-05-26
You can try dragging it.

---

### Post by mcduck on 2009-05-27
> **Sarai the Geek said:**
> Install Ubuntu Tweak:

```
sudo apt-get install ubuntu-tweak
```Run it (it's in system tools) and click the "desktop" tab on the side- it gives you an option to enable a trash can icon on the desktop!

By the way, I agree, it is sort of an annoyance that a lot of these simple things require Ubuntu Tweak. UT should probably be installed by default in future versions.
They don't. Ubuntu Tweak is just a simple tool for making some popular changes that can be done with gconf-editor. You don't really need it for anything, everything it does and a lot more can be done directly from gconf-editor itself.

---

### Post by Sarai the Geek on 2009-05-27
> **mcduck said:**
> They don't. Ubuntu Tweak is just a simple tool for making some popular changes that can be done with gconf-editor. You don't really need it for anything, everything it does and a lot more can be done directly from gconf-editor itself.

Ya' learn something new everyday!

---

