---
title: "Text invisible in Guake after enabling desktop effects"
date: 2011-11-17
forum: Desktop Environments
---

### Post by ahbart on 2011-11-17
I'm using gnome-classic and was playing around with the desktop effects. All well, but suddenly I noticed that Guake is no longer working normal.[IMG]http://verbeekversteege.tweakdsl.nl/Schermafdruk-Guake.png[/IMG]
The normal gnome-terminal is working properly. I can select line with the mouse, which will make it white.
Does anyone know how to fix this, because I love Guake?!
I'm using Gnome-classic on Ubuntu Natty.

Offtopic: where do I change Lubuntu to Ubuntu?

---

### Post by ahbart on 2011-11-17
The problem is that the text hides behind the panel. This is a compiz/guake problem. 
I found the solution myself:

> Open Compiz Config Settings Manager and enable Place Windows. Then, on Fixed Window Placement tab, add a line in Windows with fixed positions with:

 Positioned windows: (class=Guake.py) & (title=Guake!)
 X Positions: 0
 Y Positions: 0
Source: [link]("http://guake.org/wiki/FrequentlyAskedQuestions")

---

