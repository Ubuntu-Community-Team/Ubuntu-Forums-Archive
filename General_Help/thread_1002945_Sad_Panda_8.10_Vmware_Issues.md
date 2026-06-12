---
title: "Sad Panda: 8.10 Vmware Issues"
date: 2008-12-05
forum: General Help
---

### Post by SterLo on 2008-12-05
So I recently upgraded to 8.10
I downloaded VMware Server 1.0.6

I unpacked it.
Ran vmware-install.

Here's the output after server failed installations (the underlying issue hasn't changed):

> 
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Uninstalling the tar installation of VMware Server.

 * Stopping internet superserver xinetd                                  [ OK ] 
 * Starting internet superserver xinetd                                  [ OK ] 
inetd: no process killed
Stopping VMware services:
   Virtual machine monitor                                             done

File /usr/bin/vmware-config.pl is backed up to /usr/bin/vmware-config.pl.old.0.


The removal of VMware Server 1.0.6 build-91891 for Linux completed 
successfully. Thank you for having tried this software.

Installing the content of the package.

In which directory do you want to install the binary files? 
[/usr/bin] 

What is the directory that contains the init directories (rc0.d/ to rc6.d/)? 
[/etc] 

What is the directory that contains the init scripts? 
[/etc/init.d] 

In which directory do you want to install the daemon files? 
[/usr/sbin] 

In which directory do you want to install the library files? 
[/usr/lib/vmware]

The path "/usr/lib/vmware" does not exist currently. This program is going to 
create it, including needed parent directories. Is this what you want? 
[yes] 

In which directory do you want to install the manual files? 
[/usr/share/man] 
In which directory do you want to install the documentation files? 
[/usr/share/doc/vmware]

The path "/usr/share/doc/vmware" does not exist currently. This program is 
going to create it, including needed parent directories. Is this what you want?
[yes] 

readdir() attempted on invalid dirhandle LS at ./vmware-install.pl line 458.
closedir() attempted on invalid dirhandle LS at ./vmware-install.pl line 459.
The installation of VMware Server 1.0.6 build-91891 for Linux completed 
successfully. You can decide to remove this software from your system at any 
time by invoking the following command: "/usr/bin/vmware-uninstall.pl".

Before running VMware Server for the first time, you need to configure it by 
invoking the following command: "/usr/bin/vmware-config.pl". Do you want this 
program to invoke the command for you now? [yes]


So I am fine up to this point.
Then we start the configuration process - and every time I try to reconfigure it bombs out. I have Googled quite a bit - and the solutions I have seen haven't helped me. I was wondering if anyone else has some input.

Here's the configuration:

> 
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

You must read and accept the End User License Agreement to continue.
Press enter to display it.
Do you accept? (yes/no) y

Thank you.

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons]

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

/usr/share/applications/vmware-server.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
/usr/share/applications/vmware-console-uri-handler.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [no] yes

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.27-9-generic/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config3/vmmon-only'
make -C /lib/modules/2.6.27-9-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /tmp/vmware-config3/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config3/vmmon-only/./include/machine.h:24,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:49:
/tmp/vmware-config3/vmmon-only/./include/x86.h:830:1: warning: "PTE_PFN_MASK" redefined
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
In file included from /tmp/vmware-config3/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:71:
/tmp/vmware-config3/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
/tmp/vmware-config3/vmmon-only/linux/driver.c:146: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config3/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config3/vmmon-only/linux/driver.c:150: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config3/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config3/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config3/vmmon-only/linux/driver.c:1670: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config3/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config3/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config3/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


---

### Post by parsim on 2008-12-05
Same here.

I'm so jacked with VMWare. I paid good money for it and every damn time I go to use it, it requires re-configuration, which fails.

I have fixed, patched, and reinstalled this thing more times than I can remember. Only ever works until the next kernel upgrade.

---

