---
title: "Can't install theme's for Enlightenment (e16)"
date: 2006-01-12
forum: Desktop Environments
---

### Post by Hij on 2006-01-12
I can's install theme's for Enlightenment (e16). When I try to put a theme in "usr/share/enlightenment/themes" I get a message that I have no permission for this folder. I get this message when I use Gnome and also in Enlightenment.
For both I use the root menu
Can anybody help me and tel me what I do wrong.

[SIZE="1"]I realy like ubuntu, its my fourth linux distro, and this one I love!
I have tried Ret Had (long time ago, to hard), knoppix (live cd), Slax (small linux distro) and now Ubuntu.
Sorry for my bad English[/SIZE]

---

### Post by Ampersand on 2006-01-12
You need to copy it as root, either run a file manager using
```
sudo nautilus --no-desktop
```
(or whatever file manager you use), or in a terminal
```
sudo cp theme /usr/share/enlightenment/themes/
```
(replacing 'theme' with whatever the theme folder is called.

---

### Post by Hij on 2006-01-12
Thanks!!!
This works!

---

