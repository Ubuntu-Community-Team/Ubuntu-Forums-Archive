---
title: "nw802 webcam driver install problem"
date: 2005-12-25
forum: General Help
---

### Post by ephman on 2005-12-25
hi,

i have a dark ring usb logitech webcam that needs to use the nw802 driver, and i'm having an issue with installing it.  any help would be appreciated.

here are the instructions:
    cvs -d:pserver:anonymous@cvs.nw802.sourceforge.net:/cvsroot/nw802 login
    cvs -z3 -d:pserver:anonymous@cvs.nw802.sourceforge.net:/cvsroot/nw802
    co nw802-2.4
    cd nw802-2.4
    cp Makefile.26 Makefile
    patch -p0 < patch-2.6
    make clean
    make

when i get to "**co nw802-2.4**" command i get: "**bash: co: command not found**"

any help would be awesome i'd love to get this camera going thanks...

thanks for the bandwidth,
ephman

---

### Post by ephman on 2005-12-26
silly silly i forgot to add CVS before the CO command....

ephman

---

