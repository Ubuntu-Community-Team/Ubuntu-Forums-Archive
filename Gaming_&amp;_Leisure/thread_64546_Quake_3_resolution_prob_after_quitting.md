---
title: "Quake 3 resolution prob after quitting"
date: 2005-09-11
forum: Gaming &amp; Leisure
---

### Post by zurn on 2005-09-11
Did'nt find any threads talking about this.

Here's my problem, when I play quake3 everythings fine, but when I quit playing and return to the desktop, my desktop resolution does'nt switch back. I play quake3 in 1024x768 and my desktop is 1280x1024....

Thanks for the help!

---

### Post by Xiata on 2005-09-12
[QUOTE=zurn]Did'nt find any threads talking about this.

Here's my problem, when I play quake3 everythings fine, but when I quit playing and return to the desktop, my desktop resolution does'nt switch back. I play quake3 in 1024x768 and my desktop is 1280x1024....

Thanks for the help![/QUOTE]
 Edit your shortcut (or script) to essentially do this (of course this is assuming you have xrandr enabled in your xorg.conf):
/bin/sh -c "RESOLUTION=`xrandr | grep "*" | cut -d "*" -f 2 | cut -d " " -f 1`; quake3; /usr/bin/X11/xrandr -s $RESOLUTION"

... or something like that.

---

### Post by zurn on 2005-09-24
Thx, i'll try it....another thing thats weird..while playing if I use the left ctrl and alt keys to straff, it seems like the alt key stays frozen, so I keep straffing to the left. If i reassign the straff key to anything else, its ok!  It only does it in Gnome not KDE ....any ideas?

Thx!

---

