---
title: "Railroad Tycoon 2 Wont Open -.-"
date: 2008-07-12
forum: Gaming &amp; Leisure
---

### Post by NovruzeliH on 2008-07-12
hey guys i just downloaded railroad tycoon 2 the linux version and in the readme it tell me to put on the rt2.sh to play the game, im executing it, nothing happens -.- isnt it wiered lol ??? any1 know why it does that ?

---

### Post by DouglasCaixeta on 2008-07-13
OK, firstly you need to change to bash rather than dash.

sudo dpkg-reconfigure dash


..and say NO.

Them you need to MOUNT the CD of Railroad Tycoon, the ISO image,

Them cd /media/cdrom0

and

sudo sh setup.sh

Works?

If you install successful, try to install new maps from the internet. From here for example: [http://theterminal.dune2k.com](http://theterminal.dune2k.com).

If works, please tell me what you do, cause I don't know what to do!

---

