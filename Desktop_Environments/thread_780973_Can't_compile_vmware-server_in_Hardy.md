---
title: "Can't compile vmware-server in Hardy"
date: 2008-05-03
forum: Desktop Environments
---

### Post by bturrie on 2008-05-03
I just upgraded to Hardy. It installed kernel 2.6.24-16-386 which meant I need to recompile my vmware-server. Unfortunately the compile failed

here's what it said

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /usr/src/linux-headers-2.6.24-16-386/include/.. SUBDIRS=$PWD SRCROOT=$PW
D/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-386'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:48:
/tmp/vmware-config1/vmmon-only/./include/vm_basic_types.h:161: error: conflictin
g types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_
EPOLL" is not defined
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_
EPOLL" is not defined
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:60: error: conflicting ty                                          pes for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config1/vmmon-only/linux/driver.c:147: warning: initialization from                                           incompatible pointer type
/tmp/vmware-config1/vmmon-only/linux/driver.c:151: warning: initialization from                                           incompatible pointer type
/tmp/vmware-config1/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config1/vmmon-only/linux/driver.c:1659: error: ‘struct mm_struct’ ha                                          s no member named ‘dumpable’
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-386'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

Any suggestions?

---

### Post by macaholic on 2008-05-03
See this thread, [http://ubuntuforums.org/showthread.php?p=4868919](http://ubuntuforums.org/showthread.php?p=4868919). Hope that helps.

---

### Post by bturrie on 2008-05-03
Well that sort of worked, It compiled but it doesn't appear to run. I think I'll try compiling again.

---

