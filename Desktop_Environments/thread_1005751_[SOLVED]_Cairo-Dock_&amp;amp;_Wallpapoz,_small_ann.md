---
title: "[SOLVED] Cairo-Dock &amp;amp; Wallpapoz, small annoyance"
date: 2008-12-08
forum: Desktop Environments
---

### Post by kestrel1 on 2008-12-08
I use Cairo-Dock & have just got Wallpapoz running. When wallpapoz changes the desktop background the background of cairo-dock stays as it was.
I will try to explain better.
Cairo's background is set to transparent, so when the background changes for the main part of the desktop cairo still looks like it has the previous background loaded. It will change if I hover the mouse pointer over cairo.
I have this same setup on a Linux Mint 5 system & the background changes in the dock no problems.
The spec of the Mint system is actually lower than that of the Ubuntu 8.04 system. Can't understand it. Anyone else come across this?
see attached for example

---

### Post by Ng Oon-Ee on 2008-12-09
Under Cairo configuration (with Advanced options enabled) go to the System tab, scroll all the way down, and make sure 'emulates composition with fake transparency' is turned off.

---

### Post by kestrel1 on 2008-12-09
Sorry for the delay in replying. I had to wait until I got home from work before I could try your suggestion.
You were right, as I am sure you are aware. The tick box was ticked, unticked it & at the next wallpaper change the background was correct behind Cairo-Dock.
Thanks very much for that one. You are a star.

---

### Post by Ng Oon-Ee on 2008-12-09
You are welcome. I'm of the opinion 'emulate composition' should never be an option anyway. The most modern Metacity already enables composition, as does Compiz (of course) and whatever KDE's WM is called. Emulating composition just confuses people, and only looks nice in the static case, as you've found.

Glad to help.

---

