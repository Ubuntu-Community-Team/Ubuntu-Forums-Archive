---
title: "Fonts' size difference in gnome-terminal between GNOME and XFCE"
date: 2005-04-12
forum: Desktop Environments
---

### Post by malte on 2005-04-12
I have this strange behaviour: when I'm using GNOME my selected terminal font size and the actual gnome-terminal font do match, when I use XFCE they don't, even if the rest of the fonts are correctly rendered.

```
malte@ubuntu ~ $ xdpyinfo |grep resolution
resolution:  96x96 dots per inch
```
I attach an image to show what I mean:

[IMG]http://civis.altervista.org/Schermata3.jpg[/IMG]

I don't know what to do!

EDIT:
I found it to be a Vte bug: [http://www.os-cillation.de/cgi-bin/yabb/YaBB.cgi?board=Terminal_Help;action=display;num=1111793440](http://www.os-cillation.de/cgi-bin/yabb/YaBB.cgi?board=Terminal_Help;action=display;num=1111793440)

---

### Post by illmonkey on 2005-04-16
I have the same problem... How can I resolved it?

thank you

---

### Post by taygan on 2005-04-18
You could try Monospace 12 instead of Monospace 11 in gnome-terminal.

---

### Post by illmonkey on 2005-04-20
It work just for the terminal...

But for firefox... My desktop icons the police are too little

I don't found how to deal with this  problem... ca someone help me???

thank you

---

