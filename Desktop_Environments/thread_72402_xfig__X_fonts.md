---
title: "xfig / X /fonts"
date: 2005-10-06
forum: Desktop Environments
---

### Post by basvg on 2005-10-06
Hi,

Yesterday I had to create a new xfig file for my dissertation on my laptop. Upon startup, xfig complained about not being able to find certain fonts. Indeed, when I started to enter text it appeared that xfig couldn't find a single font.

At first I thought I was missing fonts but a check learned that I had most of the essential packages installed (i.e. msttcorefonts, ttf-things and xfonts-things). Even more, the paths to the directories containing these fonts are listed in xorg.conf. Just to be on the safe side I made sure that each  directory has a fonts.dir entry. After runing 'xset fp rehash' xfig seemed to work just fine. Great. After rebooting/ restarting X, however, the same problem occured again: xfig couldn't find its fonts. 

Just to be on the safe side I used a second machine (also running Hoary) to verify that it wasn't a machine-specific problem.
After googling again I learned that 'xset fp rehash' is supposed to be permanent in the sense that X should remember which fonts it has after a reboot/ restart. On a debian mailinglist (entry from 2004) someone had the exact same problem. His fix was to make sure that the 'xset fp rehash' command is run each time X starts using gnome-session-properties. Surely this works but it feels like a hack. Does anyone know how to solve the problem *properly*? Am I missing something? Any pointers are greatly appreciated.


Bas

---

