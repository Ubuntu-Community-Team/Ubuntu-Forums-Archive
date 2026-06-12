---
title: "debconf is weird after switching to kde"
date: 2006-07-26
forum: Desktop Environments
---

### Post by schmakk on 2006-07-26
dpkg-preconfigure: cannot connect to X server
debconf: unable to initialize frontend: Kde
debconf: (DISPLAY problem?)
debconf: falling back to frontend: Dialog

That is what i get. To begin with, it complained about not being able to talk to gnome and suggested that i checked if a certain gnome thing (library?) was installed. I did dpkg-reconfigure debconf and changed frontend to kde to correct it.

To begin with, it complained that a kde lib wasnt installed, but after installing it, this is what i get.

I assume nothing bad happens because of this, but its fairly annoying to see it almost every time i install or remove anything.

(Sorry if im in the wrong forum)

---

