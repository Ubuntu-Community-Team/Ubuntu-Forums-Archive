---
title: "ubuntu 12.04 gnome-shell Selected FG / BG color problem"
date: 2012-06-09
forum: Desktop Environments
---

### Post by dtr29 on 2012-06-09
I have recently installed ubuntu 12.04 and have swithed to the 'classic' gnome shell, however the colour scheme leaves much to be desired. I tried to modify in particular the selected forground and background colors... the background color is a dark orange and the forground color is pale. This results in too much contrast on an active selected line, and too little contrast on an inactive selected line (particularly annoying in eclipse).
I was able to change this by editing settings.ini in /usr/share/themes/Ambiance/gtk-3.0, in the sense that the change shows up on my desktop. The change however does not show up in eclipse, where it is really needed, and possibly in other applications as well. Is there an additional setting somewhere I need to change ?

---

### Post by dtr29 on 2012-06-10
Ok.... seems even when you have gtk-3.0 installed, most applications look at the gtk-2.0 settings. so you have to change gtk2.0/gtkrc as well.

---

