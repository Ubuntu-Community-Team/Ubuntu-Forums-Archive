---
title: "VMWare Player on Ubuntu 8.10 --&gt; Problem with vmmon module"
date: 2008-11-14
forum: Desktop Environments
---

### Post by Melstar on 2008-11-14
Hi,

I'm trying to install VMWare Player on Ubuntu 8.10 with the 2.6.27-7-generic kernel.

I have a problem with the vmmon module when trying configuring... The C compiler won't set the module right....

Here are some terminal output :




**vmware-config.pl**

Making sure services for VMware Player are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the theme icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Player is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] y

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.27-7-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config3/vmmon-only'
make -C /lib/modules/2.6.27-7-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /tmp/vmware-config3/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config3/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:83:
/tmp/vmware-config3/vmmon-only/./include/vm_basic_types.h:170: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config3/vmmon-only/./include/x86.h:23,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:84:
/tmp/vmware-config3/vmmon-only/./include/x86cpuid.h:383:1: warning: "BIT_MASK" redefined
In file included from include/linux/kernel.h:15,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:11:
include/linux/bitops.h:7:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config3/vmmon-only/./include/x86.h:24,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:84:
/tmp/vmware-config3/vmmon-only/./include/x86paging.h:61:1: warning: "PTE_PFN_MASK" redefined
In file included from include/asm/paravirt.h:7,
                 from include/asm/irqflags.h:55,
                 from include/linux/irqflags.h:57,
                 from include/asm/system.h:11,
                 from include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:12:
include/asm/page.h:22:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config3/vmmon-only/./include/vmci_kernel_defs.h:26,
                 from /tmp/vmware-config3/vmmon-only/./common/vmciContext.h:19,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.h:21,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:84:
/tmp/vmware-config3/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config3/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config3/vmmon-only/./include/vmci_kernel_defs.h:26,
                 from /tmp/vmware-config3/vmmon-only/./common/vmciContext.h:19,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.h:21,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:84:
/tmp/vmware-config3/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
In file included from /tmp/vmware-config3/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:115:
/tmp/vmware-config3/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
/tmp/vmware-config3/vmmon-only/linux/driver.c:197: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config3/vmmon-only/linux/driver.c:198: warning: initialization from incompatible pointer type
/tmp/vmware-config3/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config3/vmmon-only/linux/driver.c:1802: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config3/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config3/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config3/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


Does anyone have an idea on how to do this ?

---

### Post by stnkvcmls on 2008-11-23
I had the same problem. I found [this]("http://www.insecure.ws/2008/10/20/vmware-specific-specific-55x-and-kernel-2627") and it works... Hope it helps...

edit:
I managed to compile but I couldn't install 32-bit os (xp professional). First I got this error: "Unable to change virtual machine power state: Failed to connect to peer process" because I was missing 32-bit libraries (solution in [this thread]("http://ubuntuforums.org/showthread.php?p=2990990")). After that I got this error: "Version mismatch with vmmon module: expecting 169.0, got 137.0. You have an incorrect version of the `vmmon' kernel module. Try reinstalling VMware Workstation.". I google it a little and I found [this]("http://forum.ubuntu.org.cn/viewtopic.php?f=49&t=147050&start=0&st=0&sk=t&sd=a"). It's on chinese but basically I just downloaded those three files, uninstalled vmware, install again, before configure copy those files in /usr/lib/vmware/modules/source (make backup first) and then run vmware-config.pl

Hope it helps...

---

