---
title: "kde apps in gnome"
date: 2010-09-15
forum: Desktop Environments
---

### Post by Bear number one on 2010-09-15
I use some kde applications in gnome such as k3b, basket notes, kover kreator and amarok.

These pull in a large amount of dependencies and need the occasional tweak to get them running smoothly.
Although I prefer the gnome desktop would I be any better installing the kde desktop and then running the applications from the gnome menu?
Would there be any advantage to this rather than installing them individually into gnome?

---

### Post by 3Miro on 2010-09-15
The apps will install everything that they need, anything else KDE that you install is not needed. Basically, you will not gain anything. The only way to make the apps work better is if you actually install kubuntu-desktop and switch to using KDE, but that is not what you want.

Other than that, the only thing that can make a difference is tweaking the QT settings under Gnome (but I guess you have done that already).

Is there anything specific that you are having problems with?

---

### Post by Bear number one on 2010-09-15
Thanks for the swift reply, nothing specific is causing a problem, I just wondered if there was an advantage to be had before I jumped in and installed the kde desktop. Following your reply I think I'll stick to gnome with the applications I use installed.
What are 'QT settings'?
When I say tweaking I mean installing extra software or changing settings to get sound etc working correctly, these are usually tips from the ubuntu forums.

---

### Post by 3Miro on 2010-09-15
Try typing:
```
 qtconfig 
```
in the terminal.

---

### Post by Bear number one on 2010-09-15
Ok I've typed it in and up pops a box for settings, excellent, never even knew it was there!!

I've checked in synaptic and I have qt4-qtconfig installed. Had an investigative go with the settings but nothing seems to change in the appearance of my kde apps. Did a bit of googling but it didn't bring up anything very helpful.
Maybe you could point me in the right direction to learn how to use this, thanks.

---

### Post by solar george on 2010-09-15
With qtconfig you need to save your changes (in the file menu IIRC) and restart the programs before it takes effect.
You could also install [KDE's systems settings program]("apt://systemsettings") to get all of the options you'd see in a full KDE SC/Kubuntu desktop.

---

