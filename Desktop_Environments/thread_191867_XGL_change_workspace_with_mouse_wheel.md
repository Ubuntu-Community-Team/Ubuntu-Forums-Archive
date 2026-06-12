---
title: "XGL: change workspace with mouse wheel"
date: 2006-06-08
forum: Desktop Environments
---

### Post by djvishnu on 2006-06-08
One of the main things I want when i configure a window managaer, is the ability to **do all task/workspace operations with either mouse or keyboard only**. I do not want to have to move my right hand back and forth between the mouse and keyboard if I dont have to.

I use **XGL with gnome**, and i've pretty much got the setup to what i want, except a few small issues:

**1:** Change **workspace** with mousewheel. This was possible wit xorg+gnome when I held the pointer over the workspace-switcher on the gnome-panel, but it doesn't seem to work in XGL. Does anyone know howto **a)** make this possible again? **b)** make workspace switch when i use scroll on an empty dekstop area? (like fluxbox/enlightenment)

**2:** Make key-binding aliases or somthing so that i can bind more than one keycombo to the same function (ie xgl-rotate on control-alt-left and control-alt-button4 (=mousewheel up))

Hope there is someone out there that can help me, any help would be greatly appreceated. Thank you.

PS. I try highlighting keyworks in bold to make the post easier to read, please let me know if you find this annoing

---

### Post by mcduck on 2006-06-08
1. It's not possible, but I believe somebody is already working on a patch to the rotate-plugin to alow this. The problem is that with XGL/Compiz, there actually isn't any virtual desktops, so it's not possible to change between them. Instead you got one very wide desktop that is folded around the cube..

But you can enable workspace switching when you move the pointer to screen edge.. It's in rotate-plugins settings if I remember right.

---

