---
title: "Fedora live cd will not boot"
date: 2009-01-30
forum: Fedora/RedHat and derivatives
---

### Post by Strohfeuer on 2009-01-30
Is there a way to check if the image was burned correctly?

Booting from other cd's (gparted) works well. Image was burned with Brasero Disc Burning.

image file: Fedora 10 i686

thanks in advance

---

### Post by lemming465 on 2009-02-01
It should have a disk self-test option.  If you aren't getting a boot menu, put the CD into a running system and see if it has a normal directory tree structure (burned the ISO file), or whether or not the root directory of the CD contains a single large .iso file (burned a data project with the ISO file as a regular file member).  If you've got the latter, go back and burn a different new copy using the "burn image" option.

---

