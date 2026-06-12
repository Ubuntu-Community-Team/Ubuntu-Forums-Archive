---
title: "/usr/bin/ld: cannot find -lXi"
date: 2009-04-29
forum: General Help
---

### Post by bilalshah on 2009-04-29
Hi,

I tried to compile an example from Geant4. make gives me the following error.

/usr/bin/ld: cannot find -lXi

Please share if any one has solution to this problem.

Thanks
Bilal

---

### Post by Radonballoon on 2009-06-18
you're missing the libxi-dev package:

sudo aptitude install libxi-dev

---

### Post by toxic_al on 2010-07-16
I don't know if this worked for you but it did work for me! I had some trouble finding the correct library missing and this was the one. Thanks a lot!

---

