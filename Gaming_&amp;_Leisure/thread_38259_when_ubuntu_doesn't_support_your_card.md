---
title: "when ubuntu doesn't support your card"
date: 2005-05-30
forum: Gaming &amp; Leisure
---

### Post by bobgreen5s on 2005-05-30
What do you do when ubuntu doesn't support your card? My card is a ATI Mobility Radeon 7500 and it is not listede in the supported graphics card list. I would like to enable tv-out functionality and get the fglrx drivers to work. But I can't because my card isnt supported. Is there anything I can do?


Any help is appreciated.

---

### Post by Stemp on 2005-05-30
Perhaps you could use the radeon driver for this card.
See [here](http://www.x.org/X11R6.8.2/doc/radeon.4.html)
nb : I've used it for my Radeon 9200 SE and the results were good.

---

### Post by deviant03 on 2005-06-01
I have the same card and the DRI drivers that come with Xorg on Hoary work fine for 3D, dont know about TVout though since I dont need it.

---

### Post by bobgreen5s on 2005-06-01
[QUOTE=deviant03]I have the same card and the DRI drivers that come with Xorg on Hoary work fine for 3D, dont know about TVout though since I dont need it.[/QUOTE]

yeah, I load the dri module and still get 400fps in glxgears :(

---

### Post by Rumo on 2005-06-05
Have you also edited the driver section of your /etc/xorg.conf?

Sorry, if this was a stupid question.

---

