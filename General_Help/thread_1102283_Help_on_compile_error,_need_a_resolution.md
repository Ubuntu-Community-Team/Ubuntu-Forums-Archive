---
title: "Help on compile error, need a resolution"
date: 2009-03-21
forum: General Help
---

### Post by sdowney717 on 2009-03-21
```
scott@scott-desktop:~/qc-usb-0.6.6$ sudo make all
make -C "/lib/modules/2.6.27-11-generic/build" SUBDIRS="/home/scott/qc-usb-0.6.6" modules V=1 USER_OPT="-DHAVE_UTSRELEASE_H=1"
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /home/scott/qc-usb-0.6.6/.tmp_versions ; rm -f /home/scott/qc-usb-0.6.6/.tmp_versions/*
make -f scripts/Makefile.build obj=/home/scott/qc-usb-0.6.6
  gcc -Wp,-MD,/home/scott/qc-usb-0.6.6/.qc-driver.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.27-11-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -DNOKERNEL -DHAVE_UTSRELEASE_H=1 -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_driver)"  -D"KBUILD_MODNAME=KBUILD_STR(quickcam)" -c -o /home/scott/qc-usb-0.6.6/.tmp_qc-driver.o /home/scott/qc-usb-0.6.6/qc-driver.c
In file included from /home/scott/qc-usb-0.6.6/qc-driver.c:47:
/home/scott/qc-usb-0.6.6/quickcam.h:129:1: warning: "BIT" redefined
In file included from include/linux/kernel.h:15,
                 from include/linux/cache.h:4,
                 from include/linux/time.h:7,
                 from include/linux/videodev2.h:60,
                 from include/linux/videodev.h:16,
                 from /home/scott/qc-usb-0.6.6/quickcam.h:95,
                 from /home/scott/qc-usb-0.6.6/qc-driver.c:47:
include/linux/bitops.h:6:1: warning: this is the location of the previous definition
/home/scott/qc-usb-0.6.6/qc-driver.c: In function ‘qc_i2c_init’:
/home/scott/qc-usb-0.6.6/qc-driver.c:824: error: ‘struct urb’ has no member named ‘lock’
/home/scott/qc-usb-0.6.6/qc-driver.c:825: warning: assignment from incompatible pointer type
/home/scott/qc-usb-0.6.6/qc-driver.c: In function ‘qc_isoc_start’:
/home/scott/qc-usb-0.6.6/qc-driver.c:1867: warning: assignment from incompatible pointer type
/home/scott/qc-usb-0.6.6/qc-driver.c: In function ‘qc_v4l_ioctl’:
/home/scott/qc-usb-0.6.6/qc-driver.c:2529: error: ‘struct video_device’ has no member named ‘type’
/home/scott/qc-usb-0.6.6/qc-driver.c: At top level:
/home/scott/qc-usb-0.6.6/qc-driver.c:3008: error: unknown field ‘type’ specified in initializer
/home/scott/qc-usb-0.6.6/qc-driver.c:3009: error: unknown field ‘hardware’ specified in initializer
make[2]: *** [/home/scott/qc-usb-0.6.6/qc-driver.o] Error 1
make[1]: *** [_module_/home/scott/qc-usb-0.6.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [quickcam.ko] Error 2
scott@scott-desktop:~/qc-usb-0.6.6$
```

[http://qce-ga.sourceforge.net/](http://qce-ga.sourceforge.net/)

trying to compile this

---

