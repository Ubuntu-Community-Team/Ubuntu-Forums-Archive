---
title: "GUI / Frontend to GNU R?"
date: 2006-03-03
forum: Desktop Environments
---

### Post by towsonu2003 on 2006-03-03
I tried tk, but it's weird, and I started learning R today... So, anyone knows a nice gui for R (statistics package)?

r-gnome is empty
I can't get rpy to work (I don't even know if it's supposed to help...
at least some pointers pls?
thanks

---

### Post by daageep on 2006-04-16
bump

i want to know also. or equivalently for me, how do I print a plot (graphic) using the r-base package? I was thinking about copying/pasting the graphic into gimp and printing from there, but I don't know how to copy.

Help please.

edit: i figured out how to print. read the help file for dev.print. i.e. ?dev.print

or (what i prefer) you can do 

jpeg(filename="ubuntu.jpg")
plot(x,y)
dev.off()

this will produce a jpg file under your working directory with a plot(x,y) graphic.

---

### Post by towsonu2003 on 2006-04-16
I think the gui I found afterwards (still didn't like) was lib(rcmdr) inside R, or similar (don't remember command). I remember rcmdr becasue I memorized it as r-comodore... :oops:

PS. thanks for the tip daageep :)

---

### Post by Spike the Dingo on 2008-04-17
A good R gui has been an issue for some time. The software is at the bleeding edge of statistics, thus, it lacks advanced documentation and a comprehensive GUI is nearly impossible.
But, one of the most promising GUIs that I've seen is rkward for KDE. It's still in 0.4 (0.5?) but worth having a look at. Check "rkward" in the repositories.

---

