---
title: "metacity crashes the entire system"
date: 2007-08-16
forum: Desktop Effects &amp; Customization
---

### Post by bashveank on 2007-08-16
So everything was working just fine untill a few days ago when I upgraded to Compiz 0.5.2 using the stickied guide, now whenever I kill compiz, run metacity --replace, or log off the entire system freezes, I can't alt-f2, nor switch terminals, the only thing I can do is cut the power.
I've tried deleting my .compizconfig, .metacity, and editing my .gnome2/session file and replacing compiz with metacity, when I do this metacity loads up just fine, but when I compiz --replace all the old symptoms come back.

What could be going on here?

---

### Post by cudaman73 on 2007-09-05
I'd like to bump this and say that I'm having the same problem.

---

### Post by cudaman73 on 2007-09-05
I've solved the problem.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/134809](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/134809)

says to edit the compiz exe, and turn off indirect rendering. This seems to have solved the problem for me.

---

### Post by Inxsible on 2007-09-06
you guys can look into installing fusion-icon. There is a deb floating around somewhere in this forum.

It helps in switching composite managers, so you don't have to do it via terminal. it allows easier access to CCSM and Emerald Themer

---

