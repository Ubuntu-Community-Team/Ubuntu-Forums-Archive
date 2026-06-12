---
title: "Epson Multifunction Support"
date: 2005-11-26
forum: Desktop Environments
---

### Post by grendelkhan on 2005-11-26
Picked up an Epson Stylus CX3810 - out of the box, can't scan or print.

Found a gentoo wiki entry mentioning that gimp-print5 has support for this, but Installing 5.0rc1 added no new entries for printer drivers and I can't get the latest cvs to compile.

Any suggestions?

---

### Post by grendelkhan on 2005-11-28
Solved the issue by adding debian unstable to my sourceslist, downloading the sources for gutenprint-4.3.99+cvs20051122, doing the compile, install, and then cups-genppd5.0 to create the printer files.

---

