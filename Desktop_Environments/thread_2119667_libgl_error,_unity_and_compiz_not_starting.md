---
title: "libgl error, unity and compiz not starting"
date: 2013-02-24
forum: Desktop Environments
---

### Post by vj41 on 2013-02-24
Recently, on startup, my unity and comiz have stopped working. Also, I'm seeing a lot of this error:

```

[vj]:~$ LIBGL_DEBUG=verbose /usr/lib/nux/unity_support_test -p
libGL: screen 0 does not appear to be DRI2 capable
libGL: OpenDriver: trying /usr/lib/i386-linux-gnu/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/i386-linux-gnu/dri/swrast_dri.so
libGL error: dlopen /usr/lib/i386-linux-gnu/dri/swrast_dri.so failed (/usr/lib/i386-linux-gnu/dri/swrast_dri.so: wrong ELF class: ELFCLASS32)
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/swrast_dri.so
libGL error: failed to load driver: swrast

```Can anyone please tell me cause of this problem and how to fix it? Thanks in advance.


Ubuntu Version: 12.10 64-bit
  Graphics Adapter: AMD nee ATI Madison [Radeon HD 5000M series]

---

