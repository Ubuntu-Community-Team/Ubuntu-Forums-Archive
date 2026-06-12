---
title: "Hot to create a url link to a webpage in the desktop?"
date: 2017-01-11
forum: Desktop Environments
---

### Post by matteoraggi on 2017-01-11
On windows it is easy, I just make right click and I create a new link to a web page. How to create a link to a web page on linux/lubuntu?

---

### Post by howefield on 2017-01-11
> **matteoraggi said:**
> On windows it is easy, I just make right click and I create a new link to a web page. How to create a link to a web page on linux/lubuntu?

What browser are you using, eg Chromium has a menu option.. *File > Create applications shortcuts..* which does exactly what you want if I understand correctly.

---

### Post by matteoraggi on 2017-01-11
Maybe you are right! But I can't find FILE in the menu of chromium:
[http://www.fredzone.org/wp-content/uploads/2010/06/chrome-unified-menu.png](http://www.fredzone.org/wp-content/uploads/2010/06/chrome-unified-menu.png)

A lightweight browser that give the possibility to use the password, so in order of lightweight:
- qupzilla
- chromium
- firefox

Midori instead is not saving the passwords, or I would liek to use it instead, because to me it looks ot be the more quick.

---

### Post by howefield on 2017-01-11
OK, from the unified menu do you have an option called "*Add to desktop*" in the "*Tools*" menu ?

---

### Post by Dennis N on 2017-01-11
It may depend on the Desktop Environment. For Xubuntu, using XFCE a right-click on the desktop gives the "create URL link" as one option. 

Why not make a .desktop file for the URL and place it in your Desktop folder? Here is an example:
```
[Desktop Entry]
Version=1.0
Type=Link
Name=Ubuntu Forums
Comment=
Icon=gnome-fs-bookmark
URL=https://ubuntuforums.org 
```
This gives you a hyperlink on your Desktop.

---

