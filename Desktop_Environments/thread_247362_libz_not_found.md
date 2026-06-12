---
title: "libz not found"
date: 2006-08-30
forum: Desktop Environments
---

### Post by konst88 on 2006-08-30
hello.
during a configure script i got the following error:

checking for libz... configure: error: not found.
          Possibly configure picks up an outdated version
          installed by XFree86. Remove it from your system.

          Check your installation and look into config.log

i looked at config.log but i didnt understand anything there..
thx.

---

### Post by Boris2 on 2006-08-30
Try installing zlib1g-dev
This should install you the development headers of zlib.

---

### Post by konst88 on 2006-08-31
thx. exactly what i needed.

---

