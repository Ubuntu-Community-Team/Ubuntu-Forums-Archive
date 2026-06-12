---
title: "Gens installation problem"
date: 2010-10-24
forum: Gaming &amp; Leisure
---

### Post by DoubleCross on 2010-10-24
When I try to install Gens in 10.10, I get an error in Ubuntu Software Center saying "wrong architecture 'i386'." Is there any other Sega Genesis emulator that will work?

---

### Post by DoktorSeven on 2010-10-24
Install using the commandline, with 
```
dpkg -i --force-architecture gens*.deb
```
(substitute gens*.deb for whatever the package file name is)

You will need to have all of the 32-bit compatibility libraries installed (search a package installer like Synaptic for them).

---

### Post by DoubleCross on 2010-10-25
Which packages should I be looking for specifically?

---

### Post by DoktorSeven on 2010-10-25
ia32-libs should be enough, but if you still can't run it, try other packages that begin with "ia32".

---

### Post by DoubleCross on 2010-10-28
Much obliged. Works like a champ now.

---

