---
title: "Uplink: Hacker Elite on Ubuntu 9.04"
date: 2009-08-29
forum: Gaming &amp; Leisure
---

### Post by raziel420 on 2009-08-29
So I'm currently Struggling with getting Uplink Hacker Elite installed on my fresh Ubuntu install.  It comes with a full .so style installer, but unfortunately I'm having issues trying to get it to run.  So while I'm trying to get this to work, I'm also going to list what extra packages I needed to get it to work.

libstdc++.so.5  first issue, an easy fix, just install libstdc++ 5
GCC 4.2.0  Seems to be a bit of a problem as the listed version is 4.2.2 (which causes an error, requiring 4.2.0)
Error follows
```
/usr/local/games/uplink/lib/uplink.bin.x86: /usr/local/games/uplink/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

```

Any ideas on where to go from here?

---

