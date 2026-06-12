---
title: "Can't compile kernel"
date: 2009-01-15
forum: General Help
---

### Post by _sluimers_ on 2009-01-15
I tried compiling 2.6.28.

This is what I've typed:

make-kpkg clean --revision=686
make-kpkg -initrd --revision=686 kernel_image kernel_headers modules_image

This is my error:

```

CC      drivers/acpi/executer/exnames.o
gcc: Internal error: Segmentation fault (program cc1)
Please submit a full bug report.
See <file:///usr/share/doc/gcc-4.3/README.Bugs> for instructions.
make[4]: *** [drivers/acpi/executer/exnames.o] Error 1
make[3]: *** [drivers/acpi/executer] Error 2
make[2]: *** [drivers/acpi] Error 2
make[1]: *** [drivers] Error 2

```


Do I need to report a bug, or have I done something wrong myself?

I use a VB8001 with Ubuntu Intiprid 64-bit by the way.

---

### Post by Titan8990 on 2009-01-15
Kernel compilation is typically not recommended in Ubuntu. If you are interested in compiling your own kernels, I recommend checking out Gentoo or Slackware.

---

### Post by _sluimers_ on 2009-01-15
I was just about to edit my post to write in that the reason I'm doing it is an assumption that it would fix a sound bug and graphics driver bug.


Perhaps I'm wrong but looking at: [http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.28  ]("http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.28")
and seeing:     

viafb: MAINTAINERS entry
Add maintainers for VIA UniChrome(Pro)/Chrome9 Framebuffer driver

I thought maybe that's the fix I need.

---

