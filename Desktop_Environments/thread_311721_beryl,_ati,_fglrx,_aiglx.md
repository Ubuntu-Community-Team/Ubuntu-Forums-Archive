---
title: "beryl, ati, fglrx, aiglx"
date: 2006-12-03
forum: Desktop Environments
---

### Post by numbers1thru9 on 2006-12-03
I have installed a fresh clean copy of edgy and have my radeon 9600 mobility running the fglrx drivers and have the composite set to 0 to enable direct rendering. I want to use aiglx and I followed the guide [here]("http://www.ubuntuforums.org/showthread.php?t=290841&highlight=ati+aiglx+edgy") and it beryl wont load, because it gives a no composite extension error. If i take that section out of the xorg.conf file then fglrx has the default Mesa direct rendering and then beryl wont even load. I really want this to work, does anyone know how to get it to work?

---

### Post by d3v1ant_0n3 on 2006-12-03
It appears that XGL is recommended with fglrx (due to the compositing problems).

Check [ here ](http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Edgy/GCDrivers) for some guides.

Hope that helps.

---

### Post by jasonxh on 2006-12-03
AFAIK it seems not possible to use the (fglrx + aiglx + beryl) combination. U will have to use open source driver.

I'm experiencing problems with Xgl and I also want to switch to aiglx, but my x1300 is not supported by open source driver...

---

