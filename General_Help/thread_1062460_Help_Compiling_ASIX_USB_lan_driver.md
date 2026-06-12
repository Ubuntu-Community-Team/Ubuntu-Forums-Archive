---
title: "Help Compiling ASIX USB lan driver"
date: 2009-02-06
forum: General Help
---

### Post by dothedog on 2009-02-06
I have a Kohjinsha SC3 that has a built in ASIX ax88772a USB ethernet adapter in it. I am trying to compile the driver from here: [http://www.asix.com.tw/FrootAttach/driver/AX88772_772A_178_LINUX2.6.25_Driver_v1.0.6_Source.zip](http://www.asix.com.tw/FrootAttach/driver/AX88772_772A_178_LINUX2.6.25_Driver_v1.0.6_Source.zip)

Long story but I also have opensuse 11.1 on this machine and it compiled fine on that.

The source actually only got a couple of files an asix.c and asix.h and a Makefile. The compile pukes saying it can't find usbnet.h. Looking a little closer to the asix.c file, it is looking for it with this block of code:

#include "asix.h"
//#include "usbnet.h"
#if LINUX_VERSION_CODE < KERNEL_VERSION(2,6,22)
#include <../drivers/usb/net/usbnet.h>
#else
# if LINUX_VERSION_CODE < KERNEL_VERSION(2,6,25)
#include <../drivers/net/usb/usbnet.h>
#else
#include <linux/usb/usbnet.h>
#endif
#endif

my kernel version is 2.6.24-22

looking in /usr/src/linux-headers-2.6.24-22/net/usb

KohjiSC3-Ubu:/usr/src/linux-headers-2.6.24-22/drivers/net/usb$ ll
total 24
drwxr-xr-x  2 root root  4096 2009-02-06 18:18 .
drwxr-xr-x 34 root root  4096 2009-02-06 18:18 ..
-rw-r--r--  1 root root 11688 2008-02-10 22:51 Kconfig
-rw-r--r--  1 root root   718 2008-02-10 22:51 Makefile

in /usr/src/linux-headers-2.6.24-22/usb there is no "net" directory.
 
So it appears that usbnet.h is missing from the linux-headers package? Where do I find this? Any and all help is appreciated.

DoTheDog

---

### Post by dothedog on 2009-02-07
So for some reason the usbnet.h file is missing from linux-headers-2.6.24-22. I copied /usr/src/linux-2.6.24-22/devices/usb/net/usbnet.h to
/usr/src/linux-headers-2.6.24-22/net/usb and it compiled.

---

