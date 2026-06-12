---
title: "What is the difference between all?"
date: 2010-09-24
forum: Desktop Environments
---

### Post by poleepkwa on 2010-09-24
Hi guys and girls, here`s my question - what is the difference between[COLOR=Red] GDM/Murrine/Emerald[/COLOR] and which one`s themes "work" on Ubuntu Lycid?
Also, as far as I see, the Bisigi Project has gdm login screens (I already know how to change them), but I can`t see them!
I`ll be VERY grateful if somebody can answer me ;)

---

### Post by mcduck on 2010-09-24
GDM is the program responsible of handling your desktop session and logging you in. The only point where you actually see GDM is your login screen. The themes you downloaded are probably for the old version of GDM, Ubuntu currently uses GDM2 which doesn't support that kind of themeing.

Emerald is a window decorator plugin for Compiz, and affects how your window borders look like.

Compiz is a window manager, responsible of putting running programs in windows, allowing you to move them around, minimize them etc and also drawing the window  borders. It can use several different decoration plugins, like GWD (the default) that sues MEtacity themes (Metacity is Gnome desktops own window manager, if you aren't using visual effects youa re using MEtacity as your window manager).

Murrine is a GTK theme engine. GTK is what's responsible of drawing the actual program interfaces on your screen, and can use different theme engines (allowing different look and style for all buttons, scroll bars and so on.) and themes (which define what GTK engine t use, and tells it what colors to use and spacing of the program widgets etc.)

Apart from Emerald all of these are already included in the default Ubuntu desktop.

---

