---
title: "FGRLX fails to build with kernel 3"
date: 2011-10-02
forum: Desktop Environments
---

### Post by Dalekk on 2011-10-02
When I try to install fglrx, the installation fails, and the following is written to the make log:

```
DKMS make.log for fglrx-8.840 for kernel 3.0.0-12-lowlatency (x86_64)
Mon Oct  3 11:16:01 JST 2011
AMD kernel module generator version 2.1
doing Makefile based build for kernel 2.6.x and higher
rm -rf *.c *.h *.o *.ko *.a .??* *.symvers
make -C /lib/modules/3.0.0-12-lowlatency/build SUBDIRS=/var/lib/dkms/fglrx/8.840/build/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-12-lowlatency'
  CC [M]  /var/lib/dkms/fglrx/8.840/build/2.6.x/firegl_public.o
/var/lib/dkms/fglrx/8.840/build/2.6.x/firegl_public.c:117:28: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
make[2]: *** [/var/lib/dkms/fglrx/8.840/build/2.6.x/firegl_public.o] Error 1
make[1]: *** [_module_/var/lib/dkms/fglrx/8.840/build/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-lowlatency'
make: *** [kmod_build] Error 2
build failed with return value 2
```

After trying to copy the missing file into the include folder: 

```
sudo cp src/linux-headers-2.6.38-11-generic/include/linux/smp_lock.h src/linux-headers-3.0.0-12-lowlatency/include/linux/
```

the install fails again, with the following log:

```
sh: getcwd() failed: No such file or directory
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
sh: getcwd() failed: No such file or directory
make.log: No such file or directory
```

I really don't have a clue what to do about this. Any suggestions?

---

### Post by Dalekk on 2011-10-11
Bump...

---

