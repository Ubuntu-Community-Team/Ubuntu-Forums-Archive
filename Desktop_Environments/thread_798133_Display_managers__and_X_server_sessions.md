---
title: "Display managers  and X server sessions"
date: 2008-05-17
forum: Desktop Environments
---

### Post by bcn17 on 2008-05-17
So I just installed kubuntu-kde4 on top of my 8.04 ubuntu installation via synaptic package manager. I have flirted with different flavors before and have never found/figured out what all the differences are. When I install it it asks me what I want my default-display-manager to be. Now I know this has something to do with the login screen. However- If I choose kde4 as the default and then I log in with GNOME as my session is this going to affect me in any way versus if gdm is my default-display-manager and I log in with GNOME as my session? I realize that kubuntu and ubuntu use kde and gnome respectivley but are those particular to the session or the display manager or both? 
Another way to ask my question is- AFTER i log in, choosing gnome as my session are there 2  possible configurations or 1 per default display manager? 

so... could i have 4  options before I even turn on my computer? 
   
   session: gnome       default display manager: gdm 
or session: kde         default display manager: gdm 
or session: gnome       default display manager: kde
or session: kde         default display manager: kde

or is a session with kde the same irrespective of the default display manager. likewise with a gnome session?

Sorry if this is convoluted... 
another analogy if you have taken any biology how many genotypes (mixtures of default display managers and sessions) are there and how many phenotypes (actual computer set ups I can utilize) are there when installing kubuntu and ubuntu on the same machine. :) THANKS!!

---

### Post by runesvend on 2008-05-18
The display manager is responsible for launching your desktop environment. So the programs GDM and KDM, that are display managers, launch a separate program, GNOME or KDE, which are desktop environments.

The program that controls the desktop environment is not affected by the program that chooses to launch it (it only cares about the arguments that is passed to it).

---

