---
title: "Installing VMWareServer on 8.10"
date: 2009-02-13
forum: General Help
---

### Post by Paperfairy on 2009-02-13
I've been trying to install VMWare Server for the last few hours now, but to no avail. I am using Ubuntu 8.10.

I've already patched, had to manually move some files, and now I am here:

> **Terminal]
vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

root@xxxxxx-laptop: /usr/bin/vmware-config.pl
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

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
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.27-11-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Building for VMware Server 1.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config4/vmmon-only'
make -C /lib/modules/2.6.27-11-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /tmp/vmware-config4/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config4/vmmon-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config4/vmmon-only/linux/hostif.o
/tmp/vmware-config4/vmmon-only/linux/hostif.c: In function &#8216 said:**
>   /tmp/vmware-config4/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-config4/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config4/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config4/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config4/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config4/vmmon-only/common/task.o
cc1plus: warning: command line option "-Werror-implicit-function-declaration" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wdeclaration-after-statement" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wno-pointer-sign" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
In file included from /tmp/vmware-config4/vmmon-only/common/task.c:1195:
/tmp/vmware-config4/vmmon-only/common/task_compat.h: In function &#8216;void Task_Switch_V45(VMDriver*, Vcpuid)&#8217;:
/tmp/vmware-config4/vmmon-only/common/task_compat.h:2667: warning: &#8216;sysenterState.SysenterStateV45::validEIP&#8217; may be used uninitialized in this function
/tmp/vmware-config4/vmmon-only/common/task_compat.h:2667: warning: &#8216;sysenterState.SysenterStateV45::cs&#8217; may be used uninitialized in this function
/tmp/vmware-config4/vmmon-only/common/task_compat.h:2667: warning: &#8216;sysenterState.SysenterStateV45::rsp&#8217; may be used uninitialized in this function
/tmp/vmware-config4/vmmon-only/common/task_compat.h:2667: warning: &#8216;sysenterState.SysenterStateV45::rip&#8217; may be used uninitialized in this function
  CC [M]  /tmp/vmware-config4/vmmon-only/common/vmciContext.o
  CC [M]  /tmp/vmware-config4/vmmon-only/common/vmciDatagram.o
  CC [M]  /tmp/vmware-config4/vmmon-only/common/vmciDriver.o
  CC [M]  /tmp/vmware-config4/vmmon-only/common/vmciDs.o
  CC [M]  /tmp/vmware-config4/vmmon-only/common/vmciGroup.o
  CC [M]  /tmp/vmware-config4/vmmon-only/common/vmciHashtable.o
  CC [M]  /tmp/vmware-config4/vmmon-only/common/vmciProcess.o
  CC [M]  /tmp/vmware-config4/vmmon-only/common/vmciResource.o
  CC [M]  /tmp/vmware-config4/vmmon-only/common/vmciSharedMem.o
  CC [M]  /tmp/vmware-config4/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config4/vmmon-only/vmcore/compat.o
  CC [M]  /tmp/vmware-config4/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config4/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: module vmmon.ko uses symbol 'init_mm' marked UNUSED
  CC      /tmp/vmware-config4/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config4/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config4/vmmon-only'
The module loads perfectly in the running kernel.

This program previously created the file /dev/vmmon, and was about to remove 
it.  Somebody else apparently did it already.

You have already setup networking.

Would you like to skip networking setup and keep your old settings as they are?
(yes/no) [yes] 
[b]
Extracting the sources of the vmnet module.

tar: /usr/lib/vmware/modules/source/vmnet.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
Unable to untar the "/usr/lib/vmware/modules/source/vmnet.tar" file in the 
"/tmp/vmware-config4" directory.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.[/b]



I know that vmnet.tar was there before... and it suddenly disappeared. How does one recover it, or can I download it somewhere? Thanks.

---

