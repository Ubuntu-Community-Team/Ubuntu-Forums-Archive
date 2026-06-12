---
title: "compiling linux kernel...several errors"
date: 2007-03-27
forum: Desktop Environments
---

### Post by k0mpresd on 2007-03-27
i am trying to cross-compile a kernel to boot on the xbox360 but i received some errors

help please?

> k0mpresd@k0mp:~/Desktop/linux-2.6.20$ alias smake='make ARCH=powerpc CROSS_COMPILE=powerpc64-unknown-linux-gnu-'
k0mpresd@k0mp:~/Desktop/linux-2.6.20$ PATH=/opt/crosstool/gcc-4.1.0-glibc-2.3.6/powerpc64-unknown-linux-gnu/bin:$PATH
k0mpresd@k0mp:~/Desktop/linux-2.6.20$ smake
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  CC      arch/powerpc/kernel/asm-offsets.s
  GEN     include/asm-powerpc/asm-offsets.h
  HOSTCC  scripts/genksyms/genksyms.o
  SHIPPED scripts/genksyms/lex.c
  SHIPPED scripts/genksyms/parse.h
  SHIPPED scripts/genksyms/keywords.c
  HOSTCC  scripts/genksyms/lex.o
  SHIPPED scripts/genksyms/parse.c
  HOSTCC  scripts/genksyms/parse.o
  HOSTLD  scripts/genksyms/genksyms
  CC      scripts/mod/empty.o
  HOSTCC  scripts/mod/mk_elfconfig
  MKELF   scripts/mod/elfconfig.h
  HOSTCC  scripts/mod/file2alias.o
  HOSTCC  scripts/mod/modpost.o
  HOSTCC  scripts/mod/sumversion.o
  HOSTLD  scripts/mod/modpost
  HOSTCC  scripts/kallsyms
  HOSTCC  scripts/pnmtologo
  HOSTCC  scripts/conmakehash
  HOSTCC  scripts/bin2c
  CC      init/main.o
  CHK     include/linux/compile.h
  UPD     include/linux/compile.h
  CC      init/version.o
  CC      init/do_mounts.o
  CC      init/do_mounts_rd.o
  CC      init/do_mounts_initrd.o
  LD      init/mounts.o
  CC      init/initramfs.o
  CC      init/calibrate.o
  LD      init/built-in.o
  HOSTCC  usr/gen_init_cpio
  GEN     usr/initramfs_data.cpio.gz
  AS      usr/initramfs_data.o
  LD      usr/built-in.o
  CC      arch/powerpc/kernel/semaphore.o
  CC      arch/powerpc/kernel/cputable.o
  CC      arch/powerpc/kernel/ptrace.o
  CC      arch/powerpc/kernel/syscalls.o
  CC      arch/powerpc/kernel/irq.o
  CC      arch/powerpc/kernel/align.o
  CC      arch/powerpc/kernel/signal_32.o
  CC      arch/powerpc/kernel/pmc.o
  CC      arch/powerpc/kernel/vdso.o
  CC      arch/powerpc/kernel/init_task.o
  CC      arch/powerpc/kernel/process.o
  AS      arch/powerpc/kernel/systbl.o
  CC      arch/powerpc/kernel/idle.o
  LDS     arch/powerpc/kernel/vdso32/vdso32.lds
  VDSO32A arch/powerpc/kernel/vdso32/sigtramp.o
as: unrecognized option `-maltivec'
make[2]: *** [arch/powerpc/kernel/vdso32/sigtramp.o] Error 1
make[1]: *** [arch/powerpc/kernel/vdso32] Error 2
make: *** [arch/powerpc/kernel] Error 2
k0mpresd@k0mp:~/Desktop/linux-2.6.20$ 

---

### Post by k0mpresd on 2007-03-28
forum moves fast :o

---

