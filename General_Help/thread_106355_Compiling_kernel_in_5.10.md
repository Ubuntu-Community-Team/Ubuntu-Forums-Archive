---
title: "Compiling kernel in 5.10"
date: 2005-12-20
forum: General Help
---

### Post by sephiroth111 on 2005-12-20
i attempted to compile the kernel and i got the error, i grabbed the newest tools and i also got the kubuntu desktop (not like it matters) 

the log was this:
..
  LD      arch/i386/lib/built-in.o
  CC      arch/i386/lib/bitops.o
  AS      arch/i386/lib/checksum.o
  CC      arch/i386/lib/dec_and_lock.o
  CC      arch/i386/lib/delay.o
  AS      arch/i386/lib/getuser.o
  CC      arch/i386/lib/memcpy.o
  AS      arch/i386/lib/putuser.o
  CC      arch/i386/lib/strstr.o
  CC      arch/i386/lib/usercopy.o
  AR      arch/i386/lib/lib.a
  GEN     .version
  CHK     include/linux/compile.h
  UPD     include/linux/compile.h
  CC      init/version.o
  LD      init/built-in.o
  LD      .tmp_vmlinux1
drivers/built-in.o:(.bss+0x9ff4): multiple definition of `debug'
arch/i386/kernel/built-in.o:: first defined here
drivers/built-in.o: In function `dump_stack':
: multiple definition of `dump_stack'
arch/i386/kernel/built-in.o:: first defined here
ld: Warning: size of symbol `dump_stack' changed from 22 in arch/i386/kernel/built-in.o to 37 in drivers/built-in.o
make: *** [.tmp_vmlinux1] Error 1

---

### Post by BathroomNinja on 2005-12-20
To help with troubleshooting, were you following one of the guides?  If so, which one (link please), and at what step in the guide did this happen.

---

### Post by sephiroth111 on 2005-12-20
not following a guide, i downloaded all the nessary apps to build it, and it was during the make phase. 
make xconfig
make clean
make

after everything was compiled, it displayed that above message. i do believe it was during the compression of vmlinux.

---

### Post by BathroomNinja on 2005-12-20
I'm sure you're probably not a 'noob' but Ubuntu has a few differences in it from other linux distros.  I _highly_ recomend that you follow this guide:

[http://www.ubuntuforums.org/showthread.php?t=85064](http://www.ubuntuforums.org/showthread.php?t=85064)

---

