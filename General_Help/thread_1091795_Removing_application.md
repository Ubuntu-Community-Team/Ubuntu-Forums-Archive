---
title: "Removing application"
date: 2009-03-09
forum: General Help
---

### Post by RedSingularity on 2009-03-09
How can i remove WINE and all applications related to WINE from my computer?  I want to get rid of all settings and do a nice CLEAN install.

---

### Post by Archimedes0212 on 2009-03-09
I'm fairly certain that there is an uninstall feature in the wine menu.  You just need to look around a little in the Applications -> Wine menu.  

As for removing Wine itself, you just need the following line typed in to the terminal:

sudo apt-get remove wine

That should do it!

---

### Post by LegendofTom on 2009-03-09
Sometimes other depencies are still on your computuer, so you might need to do:

sudo apt-get autoremove wine

or even:

sudo apt-get autoremove --purge wine

---

### Post by RedSingularity on 2009-03-09
Whats the difference between "apt-get remove wine*" and "apt-get autoremove wine"?

---

