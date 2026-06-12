---
title: "Xorg fails after installing new kernel"
date: 2005-06-12
forum: Desktop Environments
---

### Post by adamb10 on 2005-06-12
So I decide to install the 2.6.11-1 kernel for my Athlon CPU(Used the K7 kernel). Well all goes dandy with apt-get. I reboot into the new kernel and xorg reports a nice message:

> No Screens Found 

So how do I fix this?

Thanx

---

### Post by alastair on 2005-06-12
If you are using any proprietary video cards (e.g. ATI,NVidia etc.) then you will need to also update the "restricted" modules, graphics driver and perhaps the linux "headers" for your kernel.

---

### Post by adamb10 on 2005-06-12
So basicly I need to reinstall the nvidia drivers?

---

### Post by adamb10 on 2005-06-12
[QUOTE=adamb10]So basicly I need to reinstall the nvidia drivers?[/QUOTE]
 I now get nvidia module not found.

---

### Post by jeremy on 2005-06-13
The 2.6.11-1 kernel in the repositories is known to be buggy.

---

