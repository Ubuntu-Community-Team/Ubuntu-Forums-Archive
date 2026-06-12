---
title: "errors after installation"
date: 2009-06-15
forum: General Help
---

### Post by hugobife on 2009-06-15
Hi All
Been trying to install some drivers for a web cam
I have unziped and the last command i gave was "make all"
There seem to be a lot of error messages in the below dialog. have I got the wrong driver?
I am using 9.04
Thanks 


hugh@hugh-desktop:~/Documents/qc-usb-messenger-1.8$ make all
make -C "/lib/modules/2.6.28-11-generic/build" SUBDIRS="/home/hugh/Documents/qc-usb-messenger-1.8" modules V=1 USER_OPT="-DHAVE_UTSRELEASE_H=1"
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (        \
    echo;                                \
    echo "  ERROR: Kernel configuration is invalid.";        \
    echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";    \
    echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
    echo;                                \
    /bin/false)
mkdir -p /home/hugh/Documents/qc-usb-messenger-1.8/.tmp_versions ; rm -f /home/hugh/Documents/qc-usb-messenger-1.8/.tmp_versions/*
make -f scripts/Makefile.build obj=/home/hugh/Documents/qc-usb-messenger-1.8
  gcc -Wp,-MD,/home/hugh/Documents/qc-usb-messenger-1.8/.qc-driver.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-11-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86/include/asm/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fwrapv -DNOKERNEL -DHAVE_UTSRELEASE_H=1 -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_driver)"  -D"KBUILD_MODNAME=KBUILD_STR(qcmessenger)"  -c -o /home/hugh/Documents/qc-usb-messenger-1.8/.tmp_qc-driver.o /home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c: In function ‘qc_frame_exit’:
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:1619: error: request for member ‘counter’ in something not a structure or union
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:1630: error: request for member ‘counter’ in something not a structure or union
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c: In function ‘qc_frame_get’:
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:1659: error: request for member ‘counter’ in something not a structure or union
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:1666: error: request for member ‘counter’ in something not a structure or union
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c: In function ‘qc_v4l_poll’:
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:2625: error: ‘struct video_device’ has no member named ‘priv’
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c: In function ‘qc_v4l_open’:
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:2677: error: ‘struct video_device’ has no member named ‘priv’
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:2688: error: request for member ‘counter’ in something not a structure or union
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:2693: error: request for member ‘counter’ in something not a structure or union
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:2708: error: request for member ‘counter’ in something not a structure or union
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:2714: error: request for member ‘counter’ in something not a structure or union
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:2716: error: request for member ‘counter’ in something not a structure or union
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c: In function ‘qc_v4l_close’:
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:2742: error: ‘struct video_device’ has no member named ‘priv’
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:2750: error: request for member ‘counter’ in something not a structure or union
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:2752: error: request for member ‘counter’ in something not a structure or union
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:2767: error: request for member ‘counter’ in something not a structure or union
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:2770: error: request for member ‘counter’ in something not a structure or union
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c: In function ‘qc_v4l_read’:
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:2791: error: ‘struct video_device’ has no member named ‘priv’
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:2804: error: request for member ‘counter’ in something not a structure or union
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:2826: error: request for member ‘counter’ in something not a structure or union
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c: In function ‘qc_v4l_mmap’:
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:2848: error: ‘struct video_device’ has no member named ‘priv’
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:2855: error: request for member ‘counter’ in something not a structure or union
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:2862: error: request for member ‘counter’ in something not a structure or union
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c: In function ‘qc_v4l_ioctl’:
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:2880: error: ‘struct video_device’ has no member named ‘priv’
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:2884: error: request for member ‘counter’ in something not a structure or union
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:2898: error: ‘struct video_device’ has no member named ‘type’
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:3455: error: request for member ‘counter’ in something not a structure or union
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c: At top level:
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:3487: error: unknown field ‘type’ specified in initializer
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c: In function ‘qc_usb_init’:
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:3550: error: request for member ‘counter’ in something not a structure or union
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:3556: error: request for member ‘counter’ in something not a structure or union
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:3559: error: request for member ‘counter’ in something not a structure or union
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:3564: error: request for member ‘counter’ in something not a structure or union
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:3665: error: ‘struct input_dev’ has no member named ‘private’
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:3739: error: ‘struct video_device’ has no member named ‘priv’
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:3772: error: request for member ‘counter’ in something not a structure or union
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:3774: error: request for member ‘counter’ in something not a structure or union
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:3784: error: request for member ‘counter’ in something not a structure or union
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:3791: error: request for member ‘counter’ in something not a structure or union
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c: In function ‘qc_usb_disconnect’:
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:4060: error: request for member ‘counter’ in something not a structure or union
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:4062: error: request for member ‘counter’ in something not a structure or union
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:4075: error: request for member ‘counter’ in something not a structure or union
/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.c:4079: error: request for member ‘counter’ in something not a structure or union
make[2]: *** [/home/hugh/Documents/qc-usb-messenger-1.8/qc-driver.o] Error 1
make[1]: *** [_module_/home/hugh/Documents/qc-usb-messenger-1.8] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [qcmessenger.ko] Error 2
hugh@hugh-desktop:~/Documents/qc-usb-messenger-1.8$ # insmod ./quickcam.ko
hugh@hugh-desktop:~/Documents/qc-usb-messenger-1.8$ # insmod ./quickcam.o

---

### Post by synapsys on 2009-06-15
Try

```
sudo make all
```

and see what happens.

---

### Post by hugobife on 2009-06-15
Hi Synapsys
Thanks for your response
Tried sudo 
get the same dialog

---

### Post by synapsys on 2009-06-15
It's complaining that your kernel configuration is wrong... but you're using the latest kernel..... maybe it's an old driver...... not sure.... check this thread maybe it will help you.....

[http://ubuntuforums.org/showthread.php?t=53755](http://ubuntuforums.org/showthread.php?t=53755)

---

### Post by hugobife on 2009-06-15
Cool that looks like for me and I will have a fresh go tomorrow
thanks for your help

---

