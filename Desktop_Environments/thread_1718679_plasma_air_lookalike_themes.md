---
title: "plasma air lookalike themes"
date: 2011-03-31
forum: Desktop Environments
---

### Post by Firestarter0 on 2011-03-31
are there any themes for ubuntu 10.10 that look like the kde plasma air theme? i absolutely love its looks, but dont want to switch to kde/plasma... i like the seethrough windows, but cant seem to find a theme. are there any out there?

---

### Post by Copper Bezel on 2011-03-31
There's [a tutorial from WebUpD8]("http://www.webupd8.org/2010/05/enable-rgba-transparency-in-ubuntu-910.html") for getting that kind of transparency in Gnome. It's not as complete or as stable as KDE's, and it only applies to one set of themes (though they are quite nice.) It only applies to the GTK parts of windows, that is, the content area - you'll want to use [Emerald]("http://www.webupd8.org/2009/03/ubuntu-install-themes-emerald-compiz.html") to get transparent window frames.

---

### Post by Firestarter0 on 2011-04-01
emerald works a dream, but i tried the other bit, and when i turned the laptop back on, and the whole background was just white... i tried to change the theme and it just froze up. i uninstalled the theme package and its fine now, but i want that look.. lol.

---

### Post by Copper Bezel on 2011-04-01
Crap. I thought that tutorial explained the Nautilus bug. I'm sorry for the difficulty.

The fried background is a result of a bug caused by using Nautilus with the RGBA transparency running, which kills the desktop because Nautilus actually draws the desktop. I could have *sworn* the tutorial included a patched Nautilus to fix this.

I can't find anything on the patch by itself, now, but it's included in [Nautilus Elementary]("http://www.webupd8.org/2010/09/ubuntu-1010-nautilus-elementary-ppa.html"), so switching Nautilus to the Elementary fork should fix both the background and the hanging when RGBA is enabled.

Sorry about that, once again. I'm glad the Emerald themes worked out alright, though. = )

---

### Post by Firestarter0 on 2011-04-01
could you let me know how to get the patch? or will just using the code on that page do it fine?

---

