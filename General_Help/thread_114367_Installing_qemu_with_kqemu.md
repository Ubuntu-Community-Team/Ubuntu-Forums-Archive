---
title: "Installing qemu with kqemu"
date: 2006-01-08
forum: General Help
---

### Post by Adam Atlas on 2006-01-08
I'm trying to install the qemu emulator, with the accelerator kernel module (kqemu). I get these errors while compiling:

```
make -C kqemu
make[1]: Entering directory `/home/poliphilus/Download/qemu-0.8.0/kqemu'
make -C /usr/src/linux-headers-2.6.12-10/ M=`pwd` modules
/bin/sh: /usr/src/linux-headers-2.6.12-10/scripts/gcc-version.sh: No such file or directory
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-10'

  WARNING: Symbol version dump /usr/src/linux-headers-2.6.12-10/Module.symvers
           is missing; modules will have no dependencies and modversions.

make[3]: scripts/Makefile.build: No such file or directory
make[3]: *** No rule to make target `scripts/Makefile.build'.  Stop.
make[2]: *** [_module_/home/poliphilus/Download/qemu-0.8.0/kqemu] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-10'
make[1]: *** [kqemu.ko] Error 2
make[1]: Leaving directory `/home/poliphilus/Download/qemu-0.8.0/kqemu'
make: *** [all] Error 2
```

Is there some other package I need to install to make the linux-headers usable?

---

### Post by Adam Atlas on 2006-01-08
Never mind, I used /lib/modules/2.6.12-10-386/build/include instead and it worked.

---

### Post by simone.brunozzi on 2006-02-16
Hi Adam,
I got the same error... how can I use 
/lib/modules/2.6.12-10-386/build/include
as you say????

Also, do you think that it will work with a newer kernel (I'm using 2.6.15 in dapper drake) ??

Thanks!

---

