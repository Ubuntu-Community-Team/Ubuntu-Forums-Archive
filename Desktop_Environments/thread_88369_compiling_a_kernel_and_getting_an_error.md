---
title: "compiling a kernel and getting an error"
date: 2005-11-10
forum: Desktop Environments
---

### Post by Zeroedout on 2005-11-10
Hi, the nitro patchset was recently released for the 2.6.14 kernel, so i applied em, configured the kernel, but when i try to compile it, i get this error:
```

............
  CC      arch/i386/lib/strstr.o
  CC      arch/i386/lib/usercopy.o
  AR      arch/i386/lib/lib.a
  GEN     .version
  CHK     include/linux/compile.h
  UPD     include/linux/compile.h
  CC      init/version.o
  LD      init/built-in.o
  LD      .tmp_vmlinux1
drivers/built-in.o:(.data+0x498c): undefined reference to `cfb_fillrect'
drivers/built-in.o:(.data+0x4990): undefined reference to `cfb_copyarea'
drivers/built-in.o:(.data+0x4994): undefined reference to `cfb_imageblit'
drivers/built-in.o:(.data+0x4998): undefined reference to `soft_cursor'
make[1]: *** [.tmp_vmlinux1] Error 1
make[1]: Leaving directory `/usr/src/linux-2.6.14-nitro1'
make: *** [stamp-build] Error 2

```
Any idea what module or what else could be causing this? I've googled to death and can't find any answers.

---

### Post by Drifter on 2005-11-10
I get the same errors when I try it, so far noone has been able to give me info that corrects it.  If you find out how to correct this please let me know.
Thank you very much.

---

### Post by Zeroedout on 2005-11-12
Just incase you were not aware, nitro2 was released, so let's hope this works for us. [http://forums.gentoo.org/viewtopic-t-401300-postdays-0-postorder-asc-start-0.html]("http://forums.gentoo.org/viewtopic-t-401300-postdays-0-postorder-asc-start-0.html") I'll post back if it compiles or not.

EDIT: OKAY, it compiles and runs!!!!!!!!!!!!! Now to compile the Ati drivers, and hope it works.

---

