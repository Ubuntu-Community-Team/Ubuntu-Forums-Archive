---
title: "Error: [*] Undefined when trying to compile kernel"
date: 2009-05-18
forum: General Help
---

### Post by djpandemonium on 2009-05-18
I need to recompile the kernel for usbserial support.  I'm following [these]("http://easylinuxcds.com/blog/?p=3244") instructions, but when I get to the 'make-kpkg --initrd' part and build the kernel, it works on it for an hour or so and then stops with this error:

```
  ...
  CC [M]  lib/zlib_deflate/deflate_syms.o
  LD [M]  lib/zlib_deflate/zlib_deflate.o
  Building modules, stage 2.
  MODPOST 1785 modules
ERROR: "bttv_write_gpio" [ubuntu/lirc/lirc_gpio/lirc_gpio.ko] undefined!
ERROR: "bttv_read_gpio" [ubuntu/lirc/lirc_gpio/lirc_gpio.ko] undefined!
ERROR: "bttv_gpio_enable" [ubuntu/lirc/lirc_gpio/lirc_gpio.ko] undefined!
WARNING: modpost: Found 4 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'
make[2]: *** [__modpost] Error 1
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.28'
make: *** [debian/stamp/build/kernel] Error 2
```

I've googled the ERROR messages, and the only thing I come up with is a forum thread in Italian.  My Italian understanding is passable, and it appears that there wasn't a working resolution in that thread.

Any ideas?

---

