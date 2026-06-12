---
title: "Get rid of GNOME programs"
date: 2006-05-08
forum: Desktop Environments
---

### Post by GuitarHero on 2006-05-08
I installed Kubuntu through my full ubuntu install, and now I have a set of programs for each and its too much.  Is there a way to remove all the gnome programs I don't need anymore?  And how do I get to the Konsole all I can find is terminal.

---

### Post by user1397 on 2006-05-08
if you're sure you're only gonna use kubuntu, you can try:
```
sudo apt-get remove ubuntu-desktop
```
**BEWARE! This removes all of the core packages that came with your fresh ubuntu install!**
and then when installing gnome apps you only have to install their libraries and dependencies.
Or you could just only remove certain gnome apps, one by one. Or use synaptic... (don't use adept which is kde's version of synaptic, because it just sucks compared to synaptic:))
Konsole i believe is in System or Utilities in the KDE menu, shouldn't be too hard to find...

---

### Post by vyruss on 2006-05-08
[QUOTE=erik1397]if you're sure you're only gonna use kubuntu, you can try:
```
sudo apt-get remove ubuntu-desktop
```
**BEWARE! This removes all of the core packages that came with your fresh ubuntu install!**[/QUOTE]

No it doesn't...

---

