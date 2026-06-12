---
title: "[SOLVED] x11 errors"
date: 2008-07-03
forum: Desktop Environments
---

### Post by absolutezero1287 on 2008-07-03
I made my own custom build using debootstrap but I can't get X to start. I have a copy of xorg.0.log.

---

### Post by adam_kimber on 2008-07-03
> Fatal server error:
No valid FontPath could be found

That seems to be your problem. :D 

Try using ```
Option "UseDefaultFontPath" "false"
```

Taken from here --> [Bug tracker for Ubuntu]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/173959")

---

### Post by absolutezero1287 on 2008-07-03
Problem solved! I was missing certain packages for x11, namely the xfonts.

---

### Post by adam_kimber on 2008-07-03
> **absolutezero1287 said:**
> Problem solved! I was missing certain packages for x11, namely the xfonts.

Cool can you mark the thread as solved so others who have this problem can see one solution that works?

---

