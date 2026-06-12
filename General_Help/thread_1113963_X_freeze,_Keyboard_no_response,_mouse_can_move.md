---
title: "X freeze, Keyboard no response, mouse can move"
date: 2009-04-02
forum: General Help
---

### Post by netmask254 on 2009-04-02
I suffer this problem almost every day, it happens randomly. The X lost response except a wallpaper left. No keyboard response (thus alt-ctrl-del no longer works) but mouse can move. I have no other choice but power off the laptop. Today when it happens, I remember the last key I press is F8. BTW, the ctrl+alt+[F1-F8] doesn't work on my laptop. 

Any help or guide on debugging is greatly appreciated. 

Ubuntu 8.10 AMD64
Wubi
ThinkPad X61S
Mouse and keyboard are USB connected though dock. But when it happens, it is the same for trackpoint and keyboard on laptop.

---

### Post by xenophed on 2009-04-02
I have the same problem on my sisters install if you look at /var/log/Xfree86.0.log on most systems (I use many versions of GNU/Linux)and see at the end if there is repeated linesstarting with [mi]
tried reporting it as a bug but no luck but you can search using that line.

---

### Post by xenophed on 2009-04-02
P.S. I have only seen this in ubuntu based distros a.k.a. a bug guys

---

