---
title: "Secret of Monkey Island sound problems"
date: 2009-12-18
forum: Gaming &amp; Leisure
---

### Post by Eragon0605 on 2009-12-18
I am running Monkey Island: Secret of Monkey Island in DOSBox, and the sound turns on but is very choppy, and randomly speeds up very fast and then slows down. Every once in a while the sound will work perfectly for about 5 seconds and then go back to stuttering crazily. I tried messing around with frameskip and the CPU cycles, but nothing seems to change it. This is NOT the special edition (I don't think the special edition even works in DOSBox, I think Wine is needed for that).

EDIT: Oh, and I tried running it in wine, and it won't even start up.

---

### Post by portets on 2009-12-18
read the sticky up top titled  			                          			 			[9.10 - Solution to problem with Urban Terror and other SDL-game.]("http://ubuntuforums.org/showthread.php?t=1309656")

it fixes most peoples sound issues. but mine is still messed up
[]("http://ubuntuforums.org/showthread.php?t=1309656")

---

### Post by rCXer on 2009-12-18
These problems may be because of [this known bug/glitch](https://bugs.launchpad.net/ubuntu/+source/dosbox/+bug/429373) in dosbox.  It's related to the one portets posted above.  [Here](http://ubuntuforums.org/showpost.php?p=8362674&postcount=2) are instructions that may fix it. The bug report also has many good suggestions.

---

### Post by Eragon0605 on 2009-12-18
Thanks! Entering 'sudo apt-get install libsdl1.2debian-esd' into a terminal fixed my problem.

---

### Post by kostkon on 2009-12-18
I think the MI games run best in *ScummVM*.

---

