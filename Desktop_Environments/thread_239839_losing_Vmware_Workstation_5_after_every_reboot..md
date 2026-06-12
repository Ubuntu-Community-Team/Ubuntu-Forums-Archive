---
title: "losing Vmware Workstation 5 after every reboot."
date: 2006-08-19
forum: Desktop Environments
---

### Post by cmost on 2006-08-19
Hi guys!   I'm new to Ubuntu; switching from PCLinuxOS (formerly an ardent Mepis user!)  Blah blah...

Anyway, I have installed Ubuntu 6.06.1, fully updated it and even have xgl/compiz working flawlessly (thanks to the great guides here!)

I need to use VMware Workstation 5.0 to support my clients.  I'm running the 2.6.15.26 smp capable kernel and have the correct source installed.  I ran the any-any-update 104, which allowed me to build vmware and get it up and running perfectly.  The problem is that every time I reboot, I loose vmware.  If I re-run the any-a ny-update package, it comes back.  Reboot the computer, it's gone.  I'm baffled.  I think the problem may have something to do with modules not being loaded automatically (the runme.pl script probably loads them.)  Can I modify my /etc/modules file to auto load the needed modules at every boot?  I would really appreciate a bit of help.  Otherwise, Ubuntu rules!!!  Thanks.

---

### Post by scxtt on 2006-08-19
have you taken a look int runme.pl to see if it makes any mention of the modules?

---

### Post by Dubbayoo on 2006-08-20
if you are an ATI user it is possible your libGL.so.1.2 has been overwritten with a bad version. Search the forums for that file.

---

### Post by scxtt on 2006-08-20
is that specific to workstation?  cause i have an ATI X850Pro and rebooted plenty of times using VMWare Server w/ nothing like cmost's problems ...

---

### Post by cmost on 2006-08-20
Thanks for the quick responses!  I'm using a nVidia Geforce card which is properly configured (at last as far as I know...)  I've used VMware 5 in Linux for the past year or so, without issue.  Once, with an iteration of Mepis, I had a similar problem, where Vmware would stop working at every reboot.  Someone in the mepislovers.com forum had me add a line to a file that automatically loads modules and this fixed the problem.  Sorry, I cannot recall the exact details.  Any ideas?  Thanks guys.  ;)

---

### Post by cmost on 2006-08-20
Ok, a little more information:
I added vmnet and vmmon to my /etc/modules.conf file and rebooted.
No affect on the situation.

I also tried modprobe vmnet and vmmon manually in a terminal; no luck again.

Finally, I issued the command "vmware" from a terminal to see what sort of error, if any was generated. I get this error:

"cmost@cmost-ubuntu:~$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl."

If I re-run the "runme.pl" from the any-any-update104 package it will restore my use of vmware.  Here's the output from that, in case it might be helpful...

```
Updating /usr/bin/vmware-config.pl ... already patched
Updating /usr/bin/vmware ... No patch needed/available
Updating /usr/bin/vmnet-bridge ... No patch needed/available
Updating /usr/lib/vmware/bin/vmware-vmx ... No patch needed/available
Updating /usr/lib/vmware/bin-debug/vmware-vmx ... No patch needed/available
VMware modules in "/usr/lib/vmware/modules/source" has been updated.

Before running VMware for the first time after update, you need to configure it 
for your running kernel by invoking the following command: 
"/usr/bin/vmware-config.pl". Do you want this script to invoke the command for 
you now? [yes] 

Making sure services for VMware Workstation are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   Virtual ethernet                                                    done

Configuring fallback GTK+ 2.4 libraries.

***
* Updating MIME database in /usr/share/mime...
Wrote 487 strings at 20 - 28a4
Wrote aliases at 28a4 - 2a50
Wrote parents at 2a50 - 3410
Wrote literal globs at 3410 - 346c
Wrote suffix globs at 346c - 6df4
Wrote full globs at 6df4 - 6e18
Wrote magic at 6e18 - c6c0
Wrote namespace list at c6c0 - c6d0
***
In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running 
kernel? [/lib/modules/2.6.15-26-686/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Building for VMware Workstation 5.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.15-26-686/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-686'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/task.o
cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-Wdeclaration-after-statement" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wno-pointer-sign" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-ffreestanding" is valid for C/ObjC but not for C++
include/asm/bitops.h: In function ‘int find_first_bit(const long unsigned int*, unsigned int)’:
include/asm/bitops.h:326: warning: comparison between signed and unsigned integer expressions
/tmp/vmware-config0/vmmon-only/common/task_compat.h: In function ‘void Task_Switch_V45(VMDriver*, Vcpuid)’:
/tmp/vmware-config0/vmmon-only/common/task_compat.h:1713: warning: ‘sysenterState$validEIP’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:1713: warning: ‘sysenterState$cs’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:1713: warning: ‘sysenterState$rsp’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:1713: warning: ‘sysenterState$rip’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM_V4(VMDriver*, Vcpuid) [with VMCrossPage = VMCrossPageV4]’:
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState$validEIP’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState$cs’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState$rsp’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState$rip’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMCrossPage*, VMDriver*) [with VMCrossPage = VMCrossPageGSX25]’:
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState$validEIP’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState$cs’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState$rsp’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState$rip’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMCrossPage*, VMDriver*) [with VMCrossPage = VMCrossPageGSX2]’:
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState$validEIP’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState$cs’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState$rsp’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState$rip’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMCrossPage*, VMDriver*) [with VMCrossPage = VMCrossPageV321]’:
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState$validEIP’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState$cs’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMCrossPage*, VMDriver*) [with VMCrossPage = VMCrossPageV32]’:
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState$validEIP’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState$cs’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMDriver*, Vcpuid)’:
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState$validEIP’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState$cs’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState$validEIP’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState$cs’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState$validEIP’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState$cs’ may be used uninitialized in this function
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config0/vmmon-only/vmcore/compat.o
  CC [M]  /tmp/vmware-config0/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST
  CC      /tmp/vmware-config0/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-686'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
The module loads perfectly in the running kernel.

This program previously created the file /dev/vmmon, and was about to remove it.
Somebody else apparently did it already.

This program previously created the file /dev/parport1, and was about to remove 
it.  Somebody else apparently did it already.

This program previously created the file /dev/parport2, and was about to remove 
it.  Somebody else apparently did it already.

This program previously created the file /dev/parport3, and was about to remove 
it.  Somebody else apparently did it already.

You have already setup networking.

Would you like to skip networking setup and keep your old settings as they are? 
(yes/no) [yes] 

Extracting the sources of the vmnet module.

Building the vmnet module.

Building for VMware Workstation 5.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmnet-only'
make -C /lib/modules/2.6.15-26-686/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-686'
  CC [M]  /tmp/vmware-config0/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config0/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config0/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-config0/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-config0/vmnet-only/smac_compat.o
  CC [M]  /tmp/vmware-config0/vmnet-only/smac_linux.x386.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST
  CC      /tmp/vmware-config0/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-686'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config0/vmnet-only'
The module loads perfectly in the running kernel.

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done

The configuration of VMware Workstation 5.0.0 build-13124 for Linux for this 
running kernel completed successfully.

You can now run VMware Workstation by invoking the following command: 
"/usr/bin/vmware".

Enjoy,

--the VMware team

```

Apologies for the length.  I figure any little bit of info might help.

---

### Post by scxtt on 2006-08-20
my only idea is to add vmmon (virtual machine monitor) to /etc/modules (NOT /etc/modules.conf) and give that a try ...

---

### Post by cmost on 2006-08-20
Thanks for the suggestion.  Tried it, but alas, no luck!  I wonder what gives?  Should I downgrade to an older kernel perhaps???  I can live with the 2.6.13 series if I must.  That might be more convenient than reconfiguring VMware each time I need it.

---

### Post by -deadcats on 2006-08-20
I'm running VMWare Workstation 5.5.2 in the 2.6.15.26 smp kernel with no problems. Make sure you've got gcc and g++ installed prior to compiling. Make, also. BTW, 5.5.2 is free to VMWare Workstation 5.0 owners. Just download the .tar file and extract it. Use your 5.0 registration number.

regards,
-dc

---

### Post by Dubbayoo on 2006-08-20
are vmmon and vmnet supposed to be in /etc/modules? i can't recall.

---

### Post by cmost on 2006-08-21
Well, upgraded to VMware Workstation 5.5 but again, no luck.  Everything seems to compile fine and it works...until I reboot, then it disapears again.  What the heck is going on?  This is really getting irritating!!  :confused:   Any more ideas?  Thanks again!

---

### Post by cmost on 2006-08-24
Ok guys, i've narrowed my problem down to the existence of /etc/vmware/not_configured file.  If this file is present, then vmware won't start and triggers the "please run vmware-config.pl blah blah blah..." message.  If I go in and delete this file when i reboot my computer, then VMware starts up and seem to run normally.  (I don't know why it 'thinks' it's not configured.'  Anyway, failing the root cause of why the not_configured file shows up in the first place, can someone tell me how to set Ubuntu to automatically delete this file at every reboot?  I tried setting the folder /etc/vmware, and all of its contents read only to users, groups, others, but, root can apparently write to it irregardless as the file comes back every reboot (damn file!)  Any suggestions would be greatly appreciated.  Thanks!  =D>

---

### Post by Dubbayoo on 2006-08-25
I just encountered this same issue. When you reconfigure vmware you are asked this question:

**Would you like to skip networking setup and keep your old settings as they are?**
(yes/no) [yes] no

Have you tried choosing both yes and no here?

---

### Post by cmost on 2006-08-28
I typically type no to skip the networking at this stage, since it was configured previously.  Removing VMware completeing and reinstalling it with and without the any-any-update (I've tried various versions of this from 97 to 104) to no effect.  Since I cannot seem to figure out what's happening here and since VMware apparently works fine once the not_configured file is deleted, I simply wrote a script to delete it every time I log into Gnome.  Problem solved (half-assed that is!)  :p

---

### Post by Dubbayoo on 2006-08-28
just out of curiosity do you have both vmplayer and workstation installed?

---

### Post by cmost on 2006-08-29
Actually, now that you mention it, I think I do have both player and full-blown VMware installed.  In fact, I think VMWare Player's module was used initially when I first setup VMWare; before recompiling my own module.  Perhaps I should do a full removal of the player - I won't ever use it anyway...

---

### Post by etapien on 2006-10-11
This problem is only seen on kernel 2.6.15-27-386, I had it only when using that version, after booting up with 2.6.15-26-386 I'm able to run vmware workstation with no problems, I can reboot as many times as needed and I never have to run vmware-configure.pl to run it again. so, in a nutshell, solution: make sure you're running 2.6.15-26-*

---

