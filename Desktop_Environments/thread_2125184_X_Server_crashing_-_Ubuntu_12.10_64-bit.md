---
title: "X Server crashing - Ubuntu 12.10 64-bit"
date: 2013-03-13
forum: Desktop Environments
---

### Post by shedder on 2013-03-13
I recently installed kubuntu 12.10 64-bit on a new server, and got frequent X-Server crashes. I tried changing the desktop environment to xubuntu, which seems to have helped, but I am still getting occasional crashes. It seems to happen when I mmove the mouse quickly to the bottom of the screen.

The X server backtrace is:

[614732.638] (EE) 
[614732.639] (EE) Backtrace:
[614732.645] (EE) 0: /usr/bin/X (xorg_backtrace+0x36) [0x7f53256b1b76]
[614732.646] (EE) 1: /usr/bin/X (0x7f5325509000+0x1ac9a9) [0x7f53256b59a9]
[614732.646] (EE) 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f532482f000+0xfcb0) [0x7f532483ecb0]
[614732.646] (EE) 3: /usr/lib/xorg/modules/drivers/nouveau_drv.so (0x7f532230f000+0x102e8) [0x7f532231f2e8]
[614732.646] (EE) 4: /usr/lib/xorg/modules/libshadowfb.so (0x7f53212a7000+0x22e1) [0x7f53212a92e1]
[614732.646] (EE) 5: /usr/bin/X (miPaintWindow+0x220) [0x7f5325693bc0]
[614732.646] (EE) 6: /usr/bin/X (miWindowExposures+0xc8) [0x7f5325693d08]
[614732.646] (EE) 7: /usr/bin/X (miHandleValidateExposures+0x68) [0x7f53256aa088]
[614732.646] (EE) 8: /usr/bin/X (miSlideAndSizeWindow+0x9a2) [0x7f53256aad32]
[614732.646] (EE) 9: /usr/bin/X (0x7f5325509000+0xe43cb) [0x7f53255ed3cb]
[614732.646] (EE) 10: /usr/bin/X (ConfigureWindow+0xbe0) [0x7f532558a060]
[614732.646] (EE) 11: /usr/bin/X (0x7f5325509000+0x50454) [0x7f5325559454]
[614732.646] (EE) 12: /usr/bin/X (0x7f5325509000+0x55a91) [0x7f532555ea91]
[614732.646] (EE) 13: /usr/bin/X (0x7f5325509000+0x4456a) [0x7f532554d56a]
[614732.646] (EE) 14: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7f53234b476d]
[614732.647] (EE) 15: /usr/bin/X (0x7f5325509000+0x448ad) [0x7f532554d8ad]
[614732.647] (EE) 
[614732.647] (EE) Segmentation fault at address 0x7f532210f58c
[614732.647] 
Fatal server error:
[614732.647] Caught signal 11 (Segmentation fault). Server aborting

Full X log attached.

Anyone got any suggestions to fix or work around the problem?

---

