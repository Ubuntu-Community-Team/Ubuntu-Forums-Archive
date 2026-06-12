---
title: "Driver question"
date: 2009-05-14
forum: General Help
---

### Post by GL_NORWAY on 2009-05-14
The first time I tried Ubuntu (Jaunty), it found my ethernet network device and I had 
Internet in no time. But it said something like Default or Standard on the device list, 
not the name of the controller itself. But it worked! Do I need to install its native 
driver when it works? This is an internal motherboard device and Asus actually have 
a Linux driver for it.

Installing native drivers won't compromize Linux' security in any way? It may be a 
stupid quesiton, but I just want to know.

Cheers! \\:D/

---

### Post by codysoyland on 2009-05-14
Linux comes with drivers for most ethernet cards. If it works, there's nothing to fix -- the drivers in the kernel are stable and they should be just as secure as the ones from the manufacturer.

---

### Post by mikewhatever on 2009-05-14
The driver installed is probably as native as can get. You can check what the driver is with **sudo lshw -C network**, but detection problems with ethernet are very rare, so that you'd probably want to leave it alone. As the good old saying goes, "If it ain't broken, don't fix it".

---

