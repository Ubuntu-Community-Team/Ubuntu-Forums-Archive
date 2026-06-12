---
title: "No screen output on Dell XPS One / Intel G33/G31 Integrated Graphics"
date: 2009-03-15
forum: General Help
---

### Post by northern lights on 2009-03-15
I'm trying to install Intrepid on a friend's Dell XPS One.

The installation goes fine, bootsplash works but the log-in screen and everything after is not being put out to the screen.

You can hear the sounds (at the log-in screen as well as after loggin in), so the Desktop Environment is working.

*lshw -C display* tells us it's got an Intel 82G33/G31 Express Integrated Graphics Device and that it's UNCLAIMED, i.e. no correct driver assigned.

Tried reconfiguring xserver-xorg and xfix (Recovery Mode works), but in Intrepid kinda pointless.

Any ideas on how to get rid of this black screen?

---

