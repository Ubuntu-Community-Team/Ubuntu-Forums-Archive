---
title: "Making Transparent Panel Applet Backgrounds in GTK 3.4"
date: 2012-06-02
forum: Desktop Environments
---

### Post by Destructo47 on 2012-06-02
Back when Ubuntu used GTK2, the whole process of getting the entire panel to have a custom background seemed much easier with the gtkrc file. Now, with GTK3.4's new CSS files and different folder hierarchy, this seems to have been broken. Is it really that difficult for theme designers to allow a custom background for a widget, or is that the fault of the widget designers?

Moreover, I would like to be able to modify the CSS for the Gnome Panel, but I have yet to find proper documentation on the structure of the CSS files used for GTK3.4. I don't know what the files mean by "INSENSITIVE", and other terms. What I would like to know, is how to remove theming from the Gnome Panel so as to allow for semitransparent backgrounds on the panel applets. Is this possible, or will I (and plenty of other people) have to deal with this bug?

---

### Post by Frogs Hair on 2012-06-02
Gnome Classic allows transparency through panel properties like Gnome 2 . I use the shell and have been able to find both light and dark semi transparent shell themes to my liking. Unity 3D has transparency settings for the panel while 2D does not. All desktop environments on 12.04 run on top of Gnome 3.4 so I guess it depends on which you use.

---

### Post by mmesantos1 on 2012-06-02
This will take some reading for sure, unless you know how to program in CSS. Here is a link that may be helpful to you: [https://live.gnome.org/GnomeShell/Development](https://live.gnome.org/GnomeShell/Development)

---

### Post by Giant Speck on 2012-07-07
> **Frogs Hair said:**
> Gnome Classic allows transparency through panel properties like Gnome 2 .
True, but changing the background settings for the panel does not affect the background behind certain applets, including the Indicator applet.  The background remains static.

---

