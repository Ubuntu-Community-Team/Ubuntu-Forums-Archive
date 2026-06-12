---
title: "Uninstalling ATI Driver downloaded from AMD Site"
date: 2009-06-07
forum: General Help
---

### Post by Jaded Misanthrope on 2009-06-07
I downloaded the driver for my graphics card -- the ATI X1200 -- from their site and installed it in place of the one provided by the Restricted Hardware section, but I would now like to remove it and go back to the one provided by the Restricted Hardware section; how would I do this if the driver was provided as a .run file?

---

### Post by Legace on 2009-06-07
Open Synaptic, search for **fglrx** and remove the following:
xorg-driver-fglrx
fglrx-amdcccle
fglrx-kernel-source
xorg-driver-fglrx-dev

---

### Post by Jaded Misanthrope on 2009-06-07
Thanks Legace; I didn't have the fourth package you mentioned but it doesn't seem to have made any difference. Removing the first three worked perfectly. :)

---

