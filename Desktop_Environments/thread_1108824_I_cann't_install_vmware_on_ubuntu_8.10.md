---
title: "I cann't install vmware on ubuntu 8.10"
date: 2009-03-28
forum: Desktop Environments
---

### Post by InvisibleMind on 2009-03-28
I'm trying to install vmware on ubuntu 8.10
but found error 
> 
Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config4/vmmon-only'
make -C /lib/modules/2.6.27-11-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /tmp/vmware-config4/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config4/vmmon-only/./include/machine.h:24,
                 from /tmp/vmware-config4/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config4/vmmon-only/linux/driver.c:49:
/tmp/vmware-config4/vmmon-only/./include/x86.h:830:1: warning: "PTE_PFN_MASK" redefined
In file included from include/asm/paravirt.h:7,
                 from include/asm/irqflags.h:55,
                 from include/linux/irqflags.h:57,
                 from include/asm/system.h:11,
                 from include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config4/vmmon-only/linux/driver.c:12:
include/asm/page.h:22:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config4/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config4/vmmon-only/linux/driver.c:71:
/tmp/vmware-config4/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
/tmp/vmware-config4/vmmon-only/linux/driver.c:146: error: unknown field &#8216;nopage&#8217; specified in initializer
/tmp/vmware-config4/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config4/vmmon-only/linux/driver.c:150: error: unknown field &#8216;nopage&#8217; specified in initializer
/tmp/vmware-config4/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config4/vmmon-only/linux/driver.c: In function &#8216;LinuxDriver_Ioctl&#8217;:
/tmp/vmware-config4/vmmon-only/linux/driver.c:1670: error: too many arguments to function &#8216;smp_call_function&#8217;
make[2]: *** [/tmp/vmware-config4/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config4/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config4/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

gay@gay-laptop:~/vmware-server-distrib$ 





befor compile vmware I"m trying to install

sudo apt-get install linux-headers-`uname -r` build-essential xinetd

not work and then

sudo apt-get install binutils cpp fetchmail flex gcc libarchive-zip-perl libc6-dev libcompress-zlib-perl libdb4.3-dev libpcre3 libpopt-dev lynx m4 make ncftp nmap openssl perl perl-modules unzip zip zlib1g-dev autoconf automake1.9 libtool bison autotools-dev g++ build-essential

not work
could you help me please.

---

