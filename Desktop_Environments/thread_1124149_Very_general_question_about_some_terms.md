---
title: "Very general question about some terms"
date: 2009-04-13
forum: Desktop Environments
---

### Post by Vostrocity on 2009-04-13
I'm totally confused about all the terms in the Linux world. I know in Windows there was Explorer for the shell and DWM for the extra effects. Now someone please explain to me these, I did look them up first but I still don't see what they do in the big picture.
Gnome/KDE
GTK
X Window System
Compiz

---

### Post by lloyd_b on 2009-04-13
Unix-like systems such as Linux tend to do things via "layers", and your list consists of the different layers of the GUI:

X Window system - this is the lowest level of the graphics subsystem.  It provides the actual video driver, mouse driver, etc, and assorted interfaces that programs can use to access it.

GTK/QT - These are "toolkits" that programmers use to simplify using X Windows.  They provide a consistent look-and-feel for all programs using the same toolkit, as well have supporting themes and such.  Gnome uses GTK primarily, while KDE uses QT

Gnome/KDE - These are the next layer, the "desktop environment". which provide the "window manager", handlers so that you can right click on a file and have the appropriate program started, etc.

Compiz - Eye candy layer.  Need I say more? :)

Lloyd B.

---

### Post by Vostrocity on 2009-04-13
Thanks. That was very helpful. :guitar:

---

### Post by ad_267 on 2009-04-13
A desktop environment such as Gnome or KDE also provides many different applications (setting them apart from pure window managers such as openbox and awesome). This includes stuff like the file browser, the panels, media players, configuration tools etc.

Gnome and KDE both come with a window manager. Gnome's is metacity and KDE's is kwin. Compiz is a window manager that can replace metacity and provide other fancy effects.

Yes it's confusing but you'll get used to it!

---

