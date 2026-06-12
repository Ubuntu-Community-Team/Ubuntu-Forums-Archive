---
title: "can't set xterm icon"
date: 2008-12-05
forum: Desktop Environments
---

### Post by jworr on 2008-12-05
I've been trying to set the icon for my xterm icon with this in my .Xdefaults file:

xterm*iconPixmap:/home/jworr/icons/terminal.xbm
xterm*iconMask:/home/jworr/icons/terminal-mask.xbm

however I get this warning upon starting xterm:

Warning: Cannot convert string "/home/jworr/icons/terminal.xbm" to type Pixmap
Warning: Cannot convert string "/home/jworr/icons/terminal-mask.xbm" to type Pixmap


does anyone know how to fix this?

---

### Post by kerry_s on 2008-12-05
> **jworr said:**
> I've been trying to set the icon for my xterm icon with this in my .Xdefaults file:

xterm*iconPixmap:/home/jworr/icons/terminal.xbm
xterm*iconMask:/home/jworr/icons/terminal-mask.xbm

however I get this warning upon starting xterm:

Warning: Cannot convert string "/home/jworr/icons/terminal.xbm" to type Pixmap
Warning: Cannot convert string "/home/jworr/icons/terminal-mask.xbm" to type Pixmap


does anyone know how to fix this?

use a pixmap icon?
open your terminal.xbm(bitmap) with gimp, choose save as and select pixmap. it should then be terminal.xpm which is pixmap.

---

### Post by PhilipGanchev on 2009-05-08
The same thing happens:

$ file /usr/share/pixmaps/gnome-terminal.xpm
/usr/share/pixmaps/gnome-terminal.xpm: X pixmap image text

$ cat >> ~/.Xresources
xterm*iconPixmap:/usr/share/pixmaps/gnome-terminal.xpm
^C

$ xrdb -merge ~/.Xresources

$ xterm
Warning: Cannot convert string "/usr/share/pixmaps/gnome-terminal.xpm" to type Pixmap

---

### Post by PhilipGanchev on 2010-09-26
Any more ideas??

---

