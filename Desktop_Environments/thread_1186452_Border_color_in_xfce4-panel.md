---
title: "Border color in xfce4-panel"
date: 2009-06-13
forum: Desktop Environments
---

### Post by weakhead on 2009-06-13
Hello.

How can I change border color of xfce4-panel? I guess that I need to modify my *.gtkrc-2.0/.gtkrc-2.0.mine*, but how?

---

### Post by weakhead on 2009-06-14
Bump.

---

### Post by kerry_s on 2009-06-14
look in /usr/share/themes/*

---

### Post by weakhead on 2009-06-14
> 
look in /usr/share/themes/* 

**@kerry_s**
This is location of GTK and various window manager's themes.
I'm interested in theme-independent settings. I know that I can change xfce4-panel colors in .gtkrc-2.0, but how can I override panel border settings?

---

### Post by kerry_s on 2009-06-14
if you look at the gtkrc perhaps you can see the setting you want to change.
for example i use xfce4-basic, so the setting is /usr/share/themes/Xfce-basic/gtk-2.0/gtkrc
so i copy the part i want to change to my ~/.gtkrc-2.0 and make my changes.

just a thought.

---

