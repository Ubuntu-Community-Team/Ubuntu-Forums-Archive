---
title: "Problems installing VMWare Server in Ubuntu 8.10"
date: 2008-10-26
forum: Desktop Environments
---

### Post by Aslund on 2008-10-26
Heya all

I got a bit of a problem, I had some problems with my old Ubuntu and decided to reinstall the system, as the beta was soon to end I decided to go for 8.10. 
For my project at university I need some programs and file I have at my virtual windows, but I am unable to finish the vmware server 1.0.7 installation. 
At the end I get following message: 

"Trying to find a suitable vmmon module for your running kernel.


None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 
Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.27-7-generic/build/include] 
Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.27-7-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/./include/machine.h:24,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:49:
/tmp/vmware-config0/vmmon-only/./include/x86.h:830:1: warning: "PTE_PFN_MASK" redefined
In file included from include/asm/paravirt.h:7,
                 from include/asm/irqflags.h:55,
                 from include/linux/irqflags.h:57,
                 from include/asm/system.h:11,
                 from include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:12:
include/asm/page.h:22:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config0/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:71:
/tmp/vmware-config0/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
/tmp/vmware-config0/vmmon-only/linux/driver.c:146: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config0/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c:150: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config0/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config0/vmmon-only/linux/driver.c:1670: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted."

I there anyone who can help with bringing vmware back so I can work?

---

### Post by janarene on 2008-10-26
Try giving VMware Server 2.0.0 build-116503 a shot.  I just had a flawless install on 8.10
:guitar:

---

### Post by Aslund on 2008-10-26
Hey Janarene

Maybe I should give it a shot, I just heard bad respondses on the new interface they have created in 2.0.0. Also the size on 500MB compared to 100MB is really that worth the small difference i features. 

ps. 
What about the files from the former failed installation? I have vmware spread around my root folder. 

Regards

Sebastian

---

### Post by brianfreytag on 2008-10-26
Have you tried Virtualbox?  [http://www.virtualbox.org](http://www.virtualbox.org)

I was having some issues same as you, and decided to give VirtualBox a go.  I'll never go back.  It is quick, light-weight, and does everything I need it to do.

---

### Post by Aslund on 2008-10-26
Problem is a sI wrote that I have already a virtual mashine up through vmware with information I need. So need first to get vmware up.

---

### Post by res_au on 2008-10-27
Solved:

check out [http://forum.ubuntu.org.cn/viewtopic.php?p=913873&sid=8b8d9aa85dd0ccd8ff0f4708d37d6dfd](http://forum.ubuntu.org.cn/viewtopic.php?p=913873&sid=8b8d9aa85dd0ccd8ff0f4708d37d6dfd)

it's in chinese, but you just download the 3 tar files and put them in /usr/lib/vmware/modules/source and run sudo /usr/bin/vmware-config.pl

make sure you scroll down and get the second vmmon.tar

---

### Post by Aslund on 2008-10-28
Hey res_au 

Thanks, I will look at irt, but I just installed 2.0.0 ;(
But must admit reinstalling to 1.0.7 seems temping. 

Regards

Aslund

---

### Post by Morgan86 on 2008-12-17
> **res_au said:**
> Solved:

check out [http://forum.ubuntu.org.cn/viewtopic.php?p=913873&sid=8b8d9aa85dd0ccd8ff0f4708d37d6dfd](http://forum.ubuntu.org.cn/viewtopic.php?p=913873&sid=8b8d9aa85dd0ccd8ff0f4708d37d6dfd)

it's in chinese, but you just download the 3 tar files and put them in /usr/lib/vmware/modules/source and run sudo /usr/bin/vmware-config.pl

make sure you scroll down and get the second vmmon.tar

it's works fine, thanks man!

---

