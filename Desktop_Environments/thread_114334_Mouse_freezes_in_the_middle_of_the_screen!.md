---
title: "Mouse freezes in the middle of the screen!"
date: 2006-01-08
forum: Desktop Environments
---

### Post by Rasymas on 2006-01-08
So here's the problem. As soon as I load Ubuntu, the mouse pointer freezes in the middle of the screen and doens't move at all, even after some time. Stuck. Any ideas how to solve this? :-s

---

### Post by dcstar on 2006-01-08
[QUOTE=Rasymas]So here's the problem. As soon as I load Ubuntu, the mouse pointer freezes in the middle of the screen and doens't move at all, even after some time. Stuck. Any ideas how to solve this? :-s[/QUOTE]
CTRL-ALT-F1 to get to a text login screen, then login, then:

sudo dpkg-reconfigure xserver-xorg

And pay particular attention to the Mouse section, you might have to experiment to select the correct mouse that works in your system.

---

