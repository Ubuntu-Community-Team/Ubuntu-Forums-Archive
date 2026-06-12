---
title: "ksokoban"
date: 2009-04-25
forum: Gaming &amp; Leisure
---

### Post by luislupe on 2009-04-25
Hi,

Ksokoban was supported for 8.04 but it seems it is not for 9.04 version, at least yet.

Is there a package (built with dependencies) prepared by someone?

All the other replacements for Ksokoban I tried are no good for me: xsok, gsok, berusky, enigma and rocksndiamonds.

---

### Post by junke1990 on 2009-08-19
same prob here, cant find it anywhere... :(

---

### Post by brettpim on 2009-12-19
I can't do without it either.  The Debian version should work fine:

[http://packages.debian.org/lenny/ksokoban](http://packages.debian.org/lenny/ksokoban)

you may have to start dcopserver.

---

### Post by seydou on 2010-01-01
Another option is to compile your own package, it is fairly easy, I just tried that out. Download Fedora source rpm package, strip out the source, configure the main tree and then descend to ksokoban directory and do

dh_make

followed by

dpkg-buildpackage -rfakeroot

This produces *deb package. You should have kde headers installed, and tune the source tree a bit following the error messages if any. It is better than compiling and installing whole kdegames, as it might result conflicting packages.

---

