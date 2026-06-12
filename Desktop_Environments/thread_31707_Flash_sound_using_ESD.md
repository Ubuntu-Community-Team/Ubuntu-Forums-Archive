---
title: "Flash sound using ESD?"
date: 2005-05-04
forum: Desktop Environments
---

### Post by nehalem on 2005-05-04
Is this possible?  I've just noticed that flash is very annoying in that it can't "play" with other programs.  Any way to get it to use ESD like other things?

Thanks!

---

### Post by Professor X on 2005-05-04
```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
``` worked for me.

---

