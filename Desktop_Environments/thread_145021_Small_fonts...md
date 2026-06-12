---
title: "Small fonts.."
date: 2006-03-15
forum: Desktop Environments
---

### Post by Adrian_b on 2006-03-15
I've had this problem since the beginning of Breezy and i've never found a good answer.
In GDM, when i type in my username and pass, the font is really small, the options in the sessions and actions menu's are the same small size.
In XFCE and Fluxbox, the same story..
In Gnome i do not have this problem.
I've heard some things about gnome-settings-daemon but i don't know how to implement it into the bootprocess BEFORE GDM starts because otherwise it complains about 'no display found'.

NOTE: I had a server install with xubuntu-desktop on it and there it didn't have this problem untill i installed GDM, when i removed GDM again, everything was back to normal.

---

### Post by kaamos on 2006-03-15
Try adding the bolded line to /etc/X11/xorg.conf
```
Section "Monitor"
     Identifier "Monitor"
     Option "DPMS"
     **DisplaySize 406 325**
EndSection
```
Suitable numbers might be something else for you, so try different ones.

---

### Post by Xian on 2006-03-15
A good [METHOD](http://www.advogato.org/person/robertc/diary.html?start=35) to get your display size.

---

### Post by Adrian_b on 2006-03-15
Has no effect whatsoever :(

---

### Post by Spano on 2006-03-15
See if you have a .gtkrc-2.0 in your hidden home files.  It probably reads something like this:
```
# -- THEME AUTO-WRITTEN DO NOT EDIT
include "/usr/share/themes/marble-look/gtk-2.0/gtkrc"

include "/home/daniel/.gtkrc-2.0.mine"

# -- THEME AUTO-WRITTEN DO NOT EDIT
```
If you do, and it does, then create a .gtkrc-2.0.mine file containing a line like this:
```
gtk-font-name = "helvetica medium 10"
```
Experiment with the font name and size untill you find something you like.  This works beautifully for me in Fluxbox on Breezy and might work for Xfce and Gnome.

---

