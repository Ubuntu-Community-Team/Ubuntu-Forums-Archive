---
title: "Freeze!!"
date: 2012-03-29
forum: Desktop Environments
---

### Post by AnanyaRaval on 2012-03-29
I installed Gnome 3.2 on my ubuntu 11.10 yesterday. The desktop freezes and nothing works, neither my mouse or keyboard.I have to power off and on.
can somebody suggest something.? I am new at this.

---

### Post by RJARRRPCGP on 2012-03-29
Sounds like the X.Org-disabling-the-keyboard-and-mouse issue. 

This comes from some boneheaded coding from someone at X.Org and sadly makes Microsoft look more sane. :(

I dunno exactly why this occurs, other then hal or the equivalent not becoming active. 

Sounds like it still depends on hal, but hal not being installed.

TBH, sounds like Ubuntu still uses hal and hal wasn't installed. 
Usually this occurs, because you installed command line Ubuntu and choose the desktop yourself. 

You probably need to do **sudo apt-get install hal** or **[B]hald**[/B]

---

