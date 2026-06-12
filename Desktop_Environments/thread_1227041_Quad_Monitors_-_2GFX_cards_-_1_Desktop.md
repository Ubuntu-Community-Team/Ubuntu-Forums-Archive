---
title: "Quad Monitors - 2GFX cards - 1 Desktop"
date: 2009-07-30
forum: Desktop Environments
---

### Post by juzzbott on 2009-07-30
Hey All, 

I currently have 2 GFX cards installed. A PCI-e 8600GTS and a PCI 6800, both are dual head cards. 

I have 2x24" monitors hooked up to the 8600GTS and 2x17" monitors hooked up to the 6800. (These are just 2 seperate cards, not running in SLI).

Under windows, all I had to do was check the "Expand desktop to this monitor" box, and could simply span across the 4 monitors seamlessly. 

In Ubuntu 9.04, I have downloaded the latest nVidia drivers (v180). I can enable "twin view" for the 2 24", however when I try to enable a 3rd monitor, I only get the option for "Seperate x window". and I can't expand the desktop across this screen. 

What is the "Seperate X window" option, and what is xinearma...

Or is there some other setting that I need to enable... or manually configure the xorg.conf file (not something I am looking forward to, so any suggestions there?).

Any help on this would be fantastic, and would love to get these other 2 monitors operational. 

Cheers, 
Justin

---

### Post by Dave_Connor on 2009-07-30
Xinerama allows to have 2 monitor on one card to act as one big desktop. You can set up Xinerama with 2 x sessions linking your 4 monitors together. There are plenty of guides to create your xorg.conf for Xinerama and setting up X Sessions.

---

