---
title: "Gnome Slab / Main Menu question"
date: 2009-08-01
forum: Desktop Environments
---

### Post by tw805 on 2009-08-01
Hi, first-time poster here, been using ubuntu for over 2 years now. 

Have recently installed the OpenSUSE-alike Slab menu, and think it's great. However, the Gnome-Control-Center link in the System Items is spelt "Control Centre", and not the correct "Control Center" spelling...

I know it's hardly an issue but I'd like to know where to find the text file that'll fix it!

(Using Ubuntu 8.10)

Cheers, 

Tom

---

### Post by f37u5g0d on 2009-08-01
I am pretty sure if you go to "System -> Preferences -> Main Menu" you can edit the menu there.  I am not sure where that text file might be buried ;)

---

### Post by tw805 on 2009-08-01
hi, cheers for the reply

that option edits the "custom main menu" applet, which im not using i'm afraid. the applet im using is called gnome-main-menu, or slab, and for some reason the "control center" is named "control centre", which is really bugging me!

i'll keep digging around. i found some stuff in /usr/share/gnome-main-menu folder but couldnt find what to edit...

thanks again,

Tom

---

### Post by kerry_s on 2009-09-07
just in case your still looking:

you would edit **/user/share/applications/gnomecc.desktop**

to get the "Install Software" you have to create a file.

**gksudo /usr/share/applications/package-manager.desktop**

put:

```
[Desktop Entry]
Name=Install Software
Exec=gksudo /usr/sbin/synaptic
Icon=synaptic
Type=Application
Categories=Settings;

```

to change the menu name, edit the slab-window.glade, line 1119

**gksudo /usr/share/gnome-main-menu/slab-window.glade**

hope it helps :)

---

### Post by kerry_s on 2009-09-13
just letting you know the system area is drag & drop able to, so you can move stuff to the favorites section, the from there to system, then just remove the favorite 1.

---

