---
title: "Xserver problems"
date: 2007-10-01
forum: Desktop Environments
---

### Post by markeee on 2007-10-01
hi,

i rebooted my desktop machine yesterday and since then i have been having problems with it

When i get to the login screen, i enter my user/pass and then i get a black screen with the timer, after a few seconds it reverts back to the login screen again?

if i go to a console login and login as root, i can run startx which starts gnome as user root-however if i login on a console login using a normal user (mark) and i run the same command i am presented with errors!

o
If i login as root and get into gnome i am still unable to run any applications using a normal user i.e. if i do xmms & - i am presented with:

** CRITICAL **: Unable to open display - but the command will work fine if run as the root user?


i have run dpkg-reconfigure xserver-xorg and checked xorg.conf manually-but the problems are still existant

---

### Post by idkwot on 2007-10-01
hmm, i have seen this before, ill comment again when i get back from the office

---

### Post by markeee on 2007-10-05
idkwot, don't suppose you know or remembered what it was you saw

still not sure what causes this or how to fix it

or anyone else..please help

thanks!

---

### Post by jamarsa on 2007-10-05
It may be a problem of ownership/permissions in some needed file in  the mark folder. Try:

chown -R mark:mark /home/mark

from root, and reload your session as mark

---

