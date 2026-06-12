---
title: "Video problem with intel GMA x3100 on Inspiron 1720"
date: 2008-11-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by deadpunk on 2008-11-02
Helloo i have image tearing problem while watching films.i have tried vlc and mplayer but in vain.
Here is a printscreen of the prob : [img]http://imagehoster.us/uploads/283fb3ac7a.jpg[/img]

Someone using the same graphic card may help me please.
Thanx in advance

---

### Post by nextekcarl on 2008-11-19
I'm having the same problem with that card on a 530N that I upgraded to 8.10 (first thing I did when I got it a couple weeks ago, therefore I'm not sure if it was present in 8.04) so I'm just bumping this to see if anyone has a fix for it yet. Nothing I've tried with compiz has made a difference yet. Here's my screenshot showing it in acting just moving a terminal window back and forth.

---

### Post by dixon on 2008-11-21
I've just installed intrepid and I have the same problem (X3100 GPU). There was no tearing in Hardy. So it's step back for me with intrepid :(

---

### Post by csonja on 2008-11-23
I have the same problem on Dell Inspiron 1420, integrated Intel X3100 graphics card. No problems with Hardy as well, and now it is very annoying :(.

---

### Post by deadpunk on 2008-11-24
Helloo again.
I have resolve my video problem while playing film.i change some setting in gstreamer-properties and set plugin to "X window System(x11/XShm/Xv) & Device to " Intel(R) Video Overlay".

And use mplayer to watch movies,but sometime when i start to watch film.. System crashes and the only way to get the system working again was to press the power button to shutdown and power on again :mad:

---

### Post by nextekcarl on 2008-11-24
I tried that and it may have been slightly better, but it still wasn't perfect.

---

### Post by june.itech on 2008-12-20
I also had problems with my Intel GMA X3100, I solved them following the suggestions posted here: [http://www.ubuntugeek.com/fix-for-video-playback-problem-in-compiz-fusion.html](http://www.ubuntugeek.com/fix-for-video-playback-problem-in-compiz-fusion.html)

---

