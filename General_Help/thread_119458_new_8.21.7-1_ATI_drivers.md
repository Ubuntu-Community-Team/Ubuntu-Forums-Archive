---
title: "new 8.21.7-1 ATI drivers"
date: 2006-01-19
forum: General Help
---

### Post by newuser111 on 2006-01-19
can anyone else confirm that these drivers no longer include fglrxconfig?

---

### Post by jasay on 2006-01-19
At the end of the install program it says to use "aticonfig", but it doesn't seem to be in the standard path (doesn't autocomplete or run when typed in fully).  I did find an aticonfig in /usr/X11R6/bin, but it complains about a missing library.:(

Edit: This was on breezy (hence R6) despite what my user info says about dapper (R7).

---

### Post by adam.tropics on 2006-01-19
No fglrxconfig here either. Used the aticonfig for initial config, then tweaked the xorg.conf file and all well with the world again. Incedentally aticonfig seems to just be a command line command with a shed load of options, maybe there is no more simple config program, hence the ati filesize having halfed.

---

### Post by StudioOneDJ on 2006-01-20
I get the same error for $ sudo aticonfig

aticonfig: error while loading shared libraries: libfglrx_pp.so.1: cannot open shared object file: No such file or directory

Anyone have any insite? Thanks in advance.

---

