---
title: "Cairo-Dock"
date: 2009-04-25
forum: General Help
---

### Post by Feelin_froggy8877 on 2009-04-25
I made some mod's to the  "Tux-n-Tosh" theme in cairo. Wanna go back to the original Settings and icons. But even after I do a complete removal and it says..."including user settings" When I pull that theme back up and use it, All my mod's are still in use? Where are these settings saved? How can I start from scratch?

---

### Post by ACMiller on 2009-04-25
This is just a bit of a guess, but you could try removing the cairo dock folder from the .config directory in your home folder. This is the folder where all of your settings and themes are saved. Maybe just back it up, then remove it and if it doesn't revert your settings how you want it to then you can replace it.

---

### Post by Feelin_froggy8877 on 2009-04-25
No go on that...but at least I know now where all the icons are at. Gues I can just redo everything manually. But would still like to know how to (really) start from scratch with programs...firefox is the same way.

---

### Post by fabounet on 2009-04-27
just choose the theme Tux from the theme manager, and tick the 2 options below to get the complete theme behaviour.

you can always delete the current theme :
rm -rf ~/.config/cairo-dock/current_theme
and restart the dock to get the default one.

please don't remove ~/.config/cairo-dock entirely, except if you want to start from scratch of course.
this folder contains your saved themes, extras themes, stacks, etc.

---

### Post by Feelin_froggy8877 on 2009-04-27
Well I had started with checking the 2 boxes (use themes behavior & icons) But still used my settings. Also I deleted cairo-dock completely from .config made a backup in /desktop reinstalled used tux_-n-tosh ans (still) found my settings somehow...so...I found where the icons are at for all the themes put the dir in the settings manager for (icons) and it worked fine...Love the dock..but some of the settings are squey....Like for instance, sizeing the icons. seems everything I try, I dont get the results I want.

---

### Post by fabounet on 2009-04-28
try out the last version

---

### Post by Feelin_froggy8877 on 2009-04-28
Is there an update to....Cairo-Dock (2007-2008)
 version 1.6.3.1???

---

### Post by fabounet on 2009-04-29
[http://developer.berlios.de/project/showfiles.php?group_id=8724&release_id=15624]("http://developer.berlios.de/project/showfiles.php?group_id=8724&release_id=15624")
not an official version though, but a release candidate

---

