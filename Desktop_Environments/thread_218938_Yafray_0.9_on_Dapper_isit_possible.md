---
title: "Yafray 0.9 on Dapper isit possible ??"
date: 2006-07-19
forum: Desktop Environments
---

### Post by SreckoMicic on 2006-07-19
When tryed to install new Yafray version 0.9 (from 18/07/06) it prompt me dependencies problems. So if anyone is using this Yafray version and Ubuntu Dapper please tell me how you solved this problems:

```
dpkg: dependency problems prevent configuration of yafray:
 yafray depends on libc6 (>= 2.3.6-6); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
 yafray depends on libgcc1 (>= 1:4.1.0); however:
  Version of libgcc1 on system is 1:4.0.3-1ubuntu5.
 yafray depends on libstdc++6 (>= 4.1.0); however:
  Version of libstdc++6 on system is 4.0.3-1ubuntu5.
dpkg: error processing yafray (--install):
 dependency problems - leaving unconfigured
```

By the way file is deb file and I'm trying to install it with dpkg, there is no official ubuntu package for this Yafray version last is 0.8. Is only solution to wait for Edgy if I want to use Yafray 0.9?

---

### Post by orb9220 on 2006-07-19
If it is a deb package then openit with the GDebi package installer.

gdepi
see if that works or synaptic for the libs and install those first.

Just a thought

---

