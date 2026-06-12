---
title: "Help with Freeciv Install, please."
date: 2005-12-15
forum: Gaming &amp; Leisure
---

### Post by DirtDawg on 2005-12-15
I've got an imac G3 running Hoary and which is *not* connected to the interenet. I've been interested in Freeciv lately, so looked through the [repos]("http://packages.ubuntu.com/hoary/games/"), since I need to download all packages and dependancies manually then save them on a thumbdrive.
But Freeciv is a little more complicated than most programs. I found the following:
~freeciv (1.14.2-1) (a "dummy package")
~freeciv-client-gtk
~freeciv-client-xaw3d
~freeciv-data
~freeciv-gtk
~freeciv-server
~freeciv-xaw3d
Also, there's a 2.x version in the backports. 
Since I can't play on the internet, thus no multiplayer, which packages do I need exactly? I figure the dummy package, the gtk, the client-gtk, and the data files? But do I need the server files? And what's a "xaw3d"?
Forgive me if this sounds lazy ("Why doesn't he just download 'em all!?"), but I could potentially spend hours on dependancies trying to install everything (unless I need to, of course). 
Thanks for the help!
:KS

---

### Post by Gustav on 2005-12-15
The packages you need is:
freeciv-client-gtk
freeciv-data
freeciv-server

Yes you need the server files to setup a local server that the game can be played on. (Xav3d is an alternative toolkit, you don't need it)

PS. If you want it I think that hoary-backports have Freeciv 2.0.2

---

### Post by DirtDawg on 2005-12-15
Thank You!

---

