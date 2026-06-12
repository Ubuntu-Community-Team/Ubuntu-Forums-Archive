---
title: "problems running mathematica 6.0 Kubuntu Keisty"
date: 2007-09-20
forum: Education &amp; Science
---

### Post by paulita on 2007-09-20
Hi all, I still can't make Mathematica 6.0 run in graphic mode under Kubuntu Feisty. The installation did ok and the mathkernel works fine, but when y try to run it in graphic mode everything freezes and i have to restart my computer. I've heard many people to have the same problem under Kubuntu Feisty, but no one has a solution. I'm really annoyed and frustrated about it. Can anyone help me?
Thanks

---

### Post by ebitnet on 2007-09-30
Hi, 
I don't seem to have this problem running MMA6.0 using the gnome desk-top.  I do have an issue that for some odd-reason, mathematic
opens 2 blank and un-removable windows that appear to be related to the kernel.

Also, I use a custom shell command (below) to start up mathematica
so that the splash-screen doesn't appear.  My understanding is that
for what ever reason, the splash-screen mucks up certain font resources.  

#!/bin/sh
/usr/local/bin/mathematica -noSplashScreen 

Aside, from not having the note-book files have the default mathematica icon, I've had no real problem.

Cheers, 
ebitnet

---

