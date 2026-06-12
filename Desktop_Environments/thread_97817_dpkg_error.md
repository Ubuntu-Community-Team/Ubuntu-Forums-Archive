---
title: "dpkg error?"
date: 2005-12-01
forum: Desktop Environments
---

### Post by babygigi on 2005-12-01
okay me being with Ubuntu for over 6 months decided to explore further... i'm that kinda person who reinstalls Ubuntu practically ever week cuz i play with all the files and ends up ruining something... this is one problem i keep on seeing... and i just wnat to know how to fix it... so i dnt' lose everyhting... this is the situation... i wanted to download SuperKaramba, and what happened was that i realized in needed kdm... which i downloaded but it changed my pc and i didnt' like it so i decided to go int Synaptic Package Manager and remove all traces of it.. bad decision! what happens is that  i get this error msg when i go bck into Synaptic

*E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. *

when i run it in terminal it tells me i need super user privilages.. but my user is already admin and it has everythign checked off. does anybody know how to chnage this?

---

### Post by Bachstelze on 2005-12-01
run it with sudo...

---

### Post by az on 2005-12-01
[QUOTE=HymnToLife]run it with sudo...[/QUOTE]
sudo dpkg --configure -a


You are not the administrator.  You are you.  Your priviledges escalate when you use sudo.

---

