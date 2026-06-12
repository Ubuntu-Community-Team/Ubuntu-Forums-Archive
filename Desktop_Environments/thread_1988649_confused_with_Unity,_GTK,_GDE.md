---
title: "confused with Unity, GTK, GDE"
date: 2012-05-27
forum: Desktop Environments
---

### Post by ankillito on 2012-05-27
Howdy all,

I haven't used Ubuntu for the last two years because I was off experimenting with Arch Linux and XMonad. Hey, everyone experiments in their youth. Now that I'm back running Ubuntu again, I am quite confused.

I know there was a major shift with Ubuntu 11 to Unity for the desktop environment over GDE. I assumed this mean there would be no more use of GTK+, as this was essentially part of GDE.

However, I then see forum posts and such about GTK+ themes. So... is Pangolin still using GTK? If so, why doesn't the following say no package found?
```
pkg-config --modversion gtk+-2.0
```
If not, what does Unity use to create windows?

---

### Post by wildmanne39 on 2012-05-27
Hi, yes it does but it uses GTK3.
Thanks

---

### Post by zombifier25 on 2012-05-27
What is "GDE"? If what you meant was GNOME, then yes, Ubuntu is still using it. Ubuntu just uses Unity as a desktop environment, the core of it still uses GNOME and GTK+. And Ubuntu from 11.10 has transitioned to GTK3.

---

