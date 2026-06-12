---
title: "Help -- gnome dont start"
date: 2006-02-04
forum: Desktop Environments
---

### Post by lfvo on 2006-02-04
hey

i dont now what i do, but now, my ubuntu dont start in gnome:cry: , but in the KDE it work well. when i choose gnome, it stop when is loading the panels and stop there, i cant do anything,only it show the wallpaper and the mouse:???: .
can anyone help me?

---

### Post by heimo on 2006-02-04
Not sure. But I'd try this: Log in to KDE, open terminal window and type:
```
mv .gnome2 .gnome2_bak
```
logout, try to log into Gnome. Does it work? If not, you can reverse what you did above with:
```
mv .gnome2_bak .gnome2
```

---

### Post by lfvo on 2006-02-04
its the same :( , but now it break loading "notificador de actualizaçoes" in portuguese because i dont now how say it in english, and show the 2 spaces of the bars bliking but i still cant do anything :cry:

---

### Post by AmericanDad on 2006-02-04
<a href=https://doubledayshyip.com/?ref=Litteaur>
<img src="http://doubledayshyip.com/images/banners/doubledayshyip468.gif" width="468" height="60" border="0">

---

### Post by lfvo on 2006-02-04
:confused: ????

please, can anyone help

---

### Post by lfvo on 2006-02-04
how can i reinstall the gnome? so i can have the default options.

---

### Post by dcstar on 2006-02-04
[QUOTE=heimo]Not sure. But I'd try this: Log in to KDE, open terminal window and type:
```
mv .gnome2 .gnome2_bak
```
logout, try to log into Gnome. Does it work? If not, you can reverse what you did above with:
```
mv .gnome2_bak .gnome2
```[/QUOTE]
Also rename the .gnome folder as well as the .gnome2 one, and then see if things reset when you log in again.

---

