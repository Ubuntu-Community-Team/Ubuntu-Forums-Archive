---
title: "Gnome Background / Wallpaper Cache"
date: 2010-11-14
forum: Desktop Environments
---

### Post by sge_kane on 2010-11-14
Hi folks,

does anyon know about Gnome's mechanism to cache my wallpaper?
I looked up the source code /nautilus,gnome-desktop,gdk) but didn't finally get behind it.

Where is my wallpaper stored.

Background:
As a matter of fact, Ubuntu changes the shipped backgrounds on updates and I wonder, why I still get to see my former background whose file is no longer existant. The gconf entry is still showing the non-existant file. So it must be cached somewhere/somehow.

Thanx for your hints to this in advance


Cheers

---

### Post by TomCell on 2010-11-19
cd ~/.cache/wallpaper
ls

And get all your cached wallpapers
WBR

---

### Post by sge_kane on 2010-11-20
Thanx alot! That is the place I was looking for!

Cheers

---

