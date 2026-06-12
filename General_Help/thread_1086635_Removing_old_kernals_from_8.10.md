---
title: "Removing old kernals from 8.10"
date: 2009-03-04
forum: General Help
---

### Post by wangsuda on 2009-03-04
Is there a simple method for removing kernals from 8.10? I have tried Cruft Remover, but it does nothing. Is there some terminal command script I can use? Thanks.

---

### Post by skymera on 2009-03-04
Uninstall them using Synaptic manager.

They'll end in the kernel number:

2.6.24-generic (etc etc)

Remove the older ones

---

### Post by wangsuda on 2009-03-04
> **skymera said:**
> Uninstall them using Synaptic manager.

They'll end in the kernel number:

2.6.24-generic (etc etc)

Remove the older onesThank you, that did the trick!

---

### Post by Operan on 2009-03-04
Using Terminal:
sudo apt-get remove linux-image-<Press Tab key>
All the linux kernel in your machine will appear after pressing Tab key. Then select one you want to remove. :D

---

