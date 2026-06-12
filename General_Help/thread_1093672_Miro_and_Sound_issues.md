---
title: "Miro and Sound issues"
date: 2009-03-11
forum: General Help
---

### Post by KratosCrux on 2009-03-11
I have been searching around everywhere and i simply cannot find a solution to this problem... im trying to install Miro in ubuntu, 8.10, intrepid, and i get an error when i type this into Terminal: 
sudo gedit /etc/apt/sources.list

- and paste this before the first line:
*_deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) intrepid/_*

- and then type this into terminal:
*_sudo apt-get update_*

- and then type this into terminal:
*_sudo apt-get install miro_*

The error looks like this:
[I][U]Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  miro: Depends: libxine1-plugins but it is not installable
E: Broken packages
[/U][/I]
Am i doing something wrong? is there i different code to type in? do i need to install something else to get this to work?

also, a fresh install of ubuntu [COLOR="Red"]**(mind you that this is ALL INSIDE OF VIRTUAL BOX, RUNNING ON XP 32-BIT** MEDIACENTER EDITION)[/COLOR] and i dont have any sound, i have SIGMATEL audio. i remember when i had ubuntu on my pendrive that it didnt have sound working right away, but i dont remember how to fix it. assuming i do get miro to install, i would guess that i kinda need sound to use it since that is over half of the applications benefit.

and please, if you have any **DEFINITE FIXES**, please post out exactly what to do, starting from scratch. thanks in advance (if any thanks are to be given)

---

