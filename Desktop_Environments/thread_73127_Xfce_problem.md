---
title: "Xfce problem"
date: 2005-10-08
forum: Desktop Environments
---

### Post by racecat on 2005-10-08
I loaded a box fresh with Ubuntu server, then went on to build an Xfce system with KDE and Gnome apps as needed. Trying to build the perfect beast. It all worked fine, until the background went Ubuntu brown and a right click on the desktop (which should bring up the Xfce main menu) does nothing. Xfce still has the desired background selected.

Any ideas? Next step is to try reloading Xfce. I had something similar happen when I was experimenting with Breezy. I'd hate to think this happened frequently and such drastic measures were required. My main machine is running Xfce with no prblems.

Bill

---

### Post by mctavish on 2005-10-08
Did you start nautilus? Because nautilus draws the backdrop in gnome, you need to start it from xfce using an option of some kind. nautilus --nodesktop perhaps?

---

### Post by racecat on 2005-10-08
[QUOTE=mctavish]Did you start nautilus? Because nautilus draws the backdrop in gnome, you need to start it from xfce using an option of some kind. nautilus --nodesktop perhaps?[/QUOTE]

I don't have nautilus loaded. The last couple of things I installed were msttcorefonts, libgnome2-perl (required for msttcorefonts), and flashplayer (from firefox, the version in the repository doesn't seem to work very well with msttcorefonts).

Bill

---

### Post by mctavish on 2005-10-09
Sorry, don't know then. Perhaps someone else has a suggestion...

---

### Post by astoltz on 2005-10-09
Check if xfdesktop is running.  If not, start it with ```
xfdesktop &
``` and be sure to check the "save session" box next time you log out

---

### Post by racecat on 2005-10-09
[QUOTE=astoltz]Check if xfdesktop is running.  If not, start it with ```
xfdesktop &
``` and be sure to check the "save session" box next time you log out[/QUOTE]

Perfect! Thanks.

Bill

---

### Post by Brian McConnell on 2005-10-09
[QUOTE=astoltz]Check if xfdesktop is running.  If not, start it with ```
xfdesktop &
``` and be sure to check the "save session" box next time you log out[/QUOTE]


I've been experiencing the same problem as the thread starter. I'll try this suggestion when I get home tonight. I thank you in advance ;>)

---

