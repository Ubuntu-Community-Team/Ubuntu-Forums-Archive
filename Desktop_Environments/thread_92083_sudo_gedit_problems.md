---
title: "sudo gedit problems"
date: 2005-11-18
forum: Desktop Environments
---

### Post by sal on 2005-11-18
when i do a sudo gedit on a file this is what i get in the terminal:

sudo gedit /etc/asound.conf
/bin/sh: -c: line 0: unexpected EOF while looking for matching `''
/bin/sh: -c: line 1: syntax error: unexpected end of file

anyone know how i could fix this please.
thanks.

---

### Post by Ampersand on 2005-11-18
Not come across that problem before, does it work if you run
```

sudo bash
gedit /etc/asound.conf

```
or
```
gksudo gedit /etc/asound.conf
```

---

### Post by sal on 2005-11-18
[QUOTE=Ampersand]Not come across that problem before, does it work if you run
```

sudo bash
gedit /etc/asound.conf

```
or
```
gksudo gedit /etc/asound.conf
```[/QUOTE]

first, thanks for helping. this was the output:>
samiam010203@computer-01:~$ gksudo gedit /etc/asound.conf
/home/samiam010203/.themes/Crystal dlb/gtk-2.0/gtkrc:9: Unable to find include file: "panel.rc"
/home/samiam010203/.themes/Crystal dlb/gtk-2.0/gtkrc:10: Unable to find include file: "toolbar.rc"
/home/samiam010203/.themes/Crystal dlb/gtk-2.0/gtkrc:481: Unable to locate image file in pixmap_path: "gfx/menuline.png"
/home/samiam010203/.themes/Crystal dlb/gtk-2.0/gtkrc:484: Background image options specified without filename
/home/samiam010203/.themes/Crystal dlb/gtk-2.0/gtkrc:910: Unable to locate image file in pixmap_path: "gfx/scrollbar_horizontal_insens.png"
/home/samiam010203/.themes/Crystal dlb/gtk-2.0/gtkrc:914: Background image options specified without filename
/home/samiam010203/.themes/Crystal dlb/gtk-2.0/gtkrc:939: Unable to locate image file in pixmap_path: "gfx/scrollbar_vertical_insens.png"
/home/samiam010203/.themes/Crystal dlb/gtk-2.0/gtkrc:943: Background image options specified without filename
(gedit:8392): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
/bin/sh: -c: line 0: unexpected EOF while looking for matching `''
/bin/sh: -c: line 1: syntax error: unexpected end of file
samiam010203@computer-01:~$


i have ubuntu 5.10 installed and added kubuntu-desktop as well.

---

