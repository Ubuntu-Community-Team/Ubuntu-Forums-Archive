---
title: "Maplestory. Help Please."
date: 2011-07-08
forum: Gaming &amp; Leisure
---

### Post by BulgarianBoy on 2011-07-08
Hello everyone.
I have been trying to get Maple to work on Linux for 7 hours today nothing has worked. I have been using a guide from gamerzplanet([http://www.gamerzplanet.net/forums/maple-story-general-discussion/298639-how-to-play-maplestory-on-linux.html)i](http://www.gamerzplanet.net/forums/maple-story-general-discussion/298639-how-to-play-maplestory-on-linux.html)i) am sure the guide works but I cannot get VMware workstation to install he is using i think 6.5 and I just cannot get it to install maybe I am doing it wrong which is possible. So i decided to use a VMware workstation 5.5.9 because there was a tutorial on how to install it and even with the tutorial this is what happened int he config.



Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.32-32-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-32-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:48:
/tmp/vmware-config1/vmmon-only/./include/vm_basic_types.h:103:7: warning: "__FreeBSD__" is not defined
In file included from /tmp/vmware-config1/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:48:
/tmp/vmware-config1/vmmon-only/./include/vm_basic_types.h:160: error: conflicting types for ‘uintptr_t’
include/linux/types.h:41: note: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config1/vmmon-only/./include/x86.h:20,
                 from /tmp/vmware-config1/vmmon-only/./include/machine.h:24,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/x86apic.h:79:1: warning: "APIC_BASE_MSR" redefined
In file included from /usr/src/linux-headers-2.6.32-32-generic/arch/x86/include/asm/apic.h:11,
                 from /usr/src/linux-headers-2.6.32-32-generic/arch/x86/include/asm/smp.h:13,
                 from include/linux/smp.h:36,
                 from include/linux/topology.h:33,
                 from include/linux/gfp.h:7,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:12:
/usr/src/linux-headers-2.6.32-32-generic/arch/x86/include/asm/apicdef.h:136:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config1/vmmon-only/./include/x86.h:21,
                 from /tmp/vmware-config1/vmmon-only/./include/machine.h:24,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/x86desc.h:593:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config1/vmmon-only/./include/machine.h:24,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/x86.h:830:1: warning: "PTE_PFN_MASK" redefined
In file included from /usr/src/linux-headers-2.6.32-32-generic/arch/x86/include/asm/paravirt.h:7,
                 from /usr/src/linux-headers-2.6.32-32-generic/arch/x86/include/asm/irqflags.h:60,
                 from include/linux/irqflags.h:57,
                 from /usr/src/linux-headers-2.6.32-32-generic/arch/x86/include/asm/system.h:11,
                 from /usr/src/linux-headers-2.6.32-32-generic/arch/x86/include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:12:
/usr/src/linux-headers-2.6.32-32-generic/arch/x86/include/asm/pgtable_types.h:182:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config1/vmmon-only/./include/vcpuset.h:78,
                 from /tmp/vmware-config1/vmmon-only/./include/modulecall.h:22,
                 from /tmp/vmware-config1/vmmon-only/./common/vmx86.h:18,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.h:16,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:226:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:230:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:298:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:304:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:402:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:489:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:576:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:663:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:665:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:748:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:750:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:831:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:833:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:912:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:914:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:1073:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:1077:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:1308:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:1433:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:70: note: previous declaration of ‘poll_initwait’ was here
In file included from /tmp/vmware-config1/vmmon-only/./include/vm_basic_asm.h:32,
                 from /tmp/vmware-config1/vmmon-only/./include/vm_asm.h:25,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:52:
/tmp/vmware-config1/vmmon-only/./include/vm_basic_asm_x86.h:48:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_basic_asm_x86.h:109:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_basic_asm_x86.h:278:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_basic_asm_x86.h:385:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config1/vmmon-only/./include/vm_asm.h:30,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:52:
/tmp/vmware-config1/vmmon-only/./include/vm_asm_x86.h:430:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_asm_x86.h:676:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_asm_x86.h:716:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config1/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:71:
/tmp/vmware-config1/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.c:80:
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
/tmp/vmware-config1/vmmon-only/linux/driver.c:144: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config1/vmmon-only/linux/driver.c:145: warning: initialization from incompatible pointer type
/tmp/vmware-config1/vmmon-only/linux/driver.c:148: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config1/vmmon-only/linux/driver.c:149: warning: initialization from incompatible pointer type
/tmp/vmware-config1/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config1/vmmon-only/linux/driver.c:1656: error: ‘struct task_struct’ has no member named ‘euid’
/tmp/vmware-config1/vmmon-only/linux/driver.c:1656: error: ‘struct task_struct’ has no member named ‘uid’
/tmp/vmware-config1/vmmon-only/linux/driver.c:1657: error: ‘struct task_struct’ has no member named ‘fsuid’
/tmp/vmware-config1/vmmon-only/linux/driver.c:1657: error: ‘struct task_struct’ has no member named ‘uid’
/tmp/vmware-config1/vmmon-only/linux/driver.c:1658: error: ‘struct task_struct’ has no member named ‘egid’
/tmp/vmware-config1/vmmon-only/linux/driver.c:1658: error: ‘struct task_struct’ has no member named ‘gid’
/tmp/vmware-config1/vmmon-only/linux/driver.c:1659: error: ‘struct task_struct’ has no member named ‘fsgid’
/tmp/vmware-config1/vmmon-only/linux/driver.c:1659: error: ‘struct task_struct’ has no member named ‘gid’
/tmp/vmware-config1/vmmon-only/linux/driver.c:1661: error: ‘struct mm_struct’ has no member named ‘dumpable’
/tmp/vmware-config1/vmmon-only/linux/driver.c:1672: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-32-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.




___________________________
Now my question is, is there a way to fix that and is there a easier way to play MS on Linux?
P.S. right now i am trying again with a better version 7.1.2.

---

### Post by Erik1984 on 2011-07-08
Have you tried to just run the Windows executable of MapleStory in Wine? edit: Sorry, just see it has 'garbage' status in the Wine AppDB ([http://appdb.winehq.org/objectManager.php?sClass=application&iId=2341](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2341))

---

### Post by BulgarianBoy on 2011-07-08
I got Vmware to work and install everything. I used Vmware 7.1.2 it worked but not i get this other messages that says Maplestory cannot run in a virtual machine. Mac users said that they had to change so Hkey_Machine and some strings because the video card was buggy and they got it to work. But that is for mac and I dont know how to do the in Linux. Any help please.

---

