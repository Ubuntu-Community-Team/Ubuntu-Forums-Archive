---
title: "MATE environment acting glitchy"
date: 2013-12-10
forum: Desktop Environments
---

### Post by fizzcol on 2013-12-10
Hello, 

This is my first post...
_My situation:_
I have tried to install the MATE desktop environment on two different computers, but every time i get the same glitch. The environment itself opens up, and then the window buttons at the bottom get cluttered with the phrase "starting caja" (by cluttered, i mean about a hundred little buttons), and then the computer gets the loading indicator on the mouse cursor, and starts to feel slow. I don't know what is causing this, the method I used to install was the one listed on the MATE website. I'm using ubuntu 13.04.
_Things I tried:_
I noticed that there is a file manager in the session and start-up section of the system settings, so I unchecked it, which didn't seem to have any affect.
I then proceeded to uninstall caja, because i was going to use pcmanfm as my file manager anyways. Even after uninstalling caja using "apt-get remove caja", the same issue occurred each time I login to my MATE session.

Any help is appreciated

---

### Post by fizzcol on 2013-12-11
apparently it had something to do with the package mate-desktop-environment as uninstalling that and using only the mate-core package seemed to do the trick.

---

