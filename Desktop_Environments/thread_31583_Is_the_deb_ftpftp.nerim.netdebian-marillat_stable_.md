---
title: "Is the deb ftp://ftp.nerim.net/debian-marillat stable main repository safe?"
date: 2005-05-03
forum: Desktop Environments
---

### Post by epb613 on 2005-05-03
I added to my repo list and then did an apt-get upgrade and I noticed that the two files it upgraded, libdv4 (libdv4 0.103-woody2) and libfribidi0 (libfribidi0 0.10.4-woody6), are actually Debian Woody packages. Is this going to cause a conflict with my Ubuntu system? And if I wanted, how could I downgrade to the original Ubuntu versions? Thanks!

---

### Post by Bob D. on 2005-05-03
Personally, I do use marillat for certain things but I never have those repos active when upgrading. Too big a chance of mixing packages that might do "Bad Things". I'll only go after the certain packages I want and ignore the rest.

To downgrade a package, open Synaptic, select (highlight) the package you wish to downgrade, and from the drop down menu select 'Package>Force Version'. A window will appear and in it will be a pick box where you can select the version of the package you wish to downgrade to (if one is available).

Bob

---

### Post by epb613 on 2005-05-04
Ah, very cool advice. Thanks alot!

---

