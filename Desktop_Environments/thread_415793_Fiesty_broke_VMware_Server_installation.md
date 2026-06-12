---
title: "Fiesty broke VMware Server installation"
date: 2007-04-20
forum: Desktop Environments
---

### Post by jonasd1 on 2007-04-20
I get the following message when attempting to "re-install" VMWare server's latest version.  Fiesty is completely upgraded including the new modules found in Synaptic Package Mgr.  I initially just re-ran the ./vmware-config.pl file like I did when I went from 6.06 to 6.10 but I got the same error even after removing it and re-installing it from scratch.

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

/usr/share/applications/vmware-server.desktop: warning: The 'Application' category is not defined by the desktop entry specification.  Please use one of "AudioVideo", "Audio", "Video", "Development", "Education", "Game", "Graphics", "Network", "Office", "Settings", "System", "Utility" instead
/usr/share/applications/vmware-console-uri-handler.desktop: warning: The 'Application' category is not defined by the desktop entry specification.  Please use one of "AudioVideo", "Audio", "Video", "Development", "Education", "Game", "Graphics", "Network", "Office", "Settings", "System", "Utility" instead
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-15-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.20-15-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.c:80:
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.
:confused:

---

### Post by teomatto on 2007-04-21
try this:

download [http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-any-any-update108.tar.gz](http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-any-any-update108.tar.gz)
$ tar zxvf vmware-any-any-update108.tar.gz
$ cd vmware-any-any-update108/
$ sudo ./runme.pl

i had a similiar problem with herd5 and i solved

ciao

---

### Post by wdaniels on 2007-04-26
I had the same problem and this fixed it - thank you!

---

### Post by Zuph on 2007-04-26
> **teomatto said:**
> try this:

download [http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-any-any-update108.tar.gz](http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-any-any-update108.tar.gz)
$ tar zxvf vmware-any-any-update108.tar.gz
$ cd vmware-any-any-update108/
$ sudo ./runme.pl

i had a similiar problem with herd5 and i solved

ciao

We're up to update 109, but otherwise this is the solution.

---

### Post by nvrpaul on 2007-04-26
hey guys, i tried to compile the module after instaling the 109 patch on fiesty, here is the oputput, i use the lowlatency kernel
Building the vmmon module.

Building for VMware Player 1.0.2 or 1.0.3 or VMware Workstation 5.5.2 or 5.5.3.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /usr/src/linux-headers-2.6.20-15-lowlatency/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-lowlatency'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/task.o
gcc: error trying to exec 'cc1plus': execvp: No such file or directory
make[2]: *** [/tmp/vmware-config1/vmmon-only/common/task.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-lowlatency'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.



help would be greatly appreaciated.
Thanks:guitar:

---

### Post by duhblow7 on 2007-04-27
> **nvrpaul said:**
> hey guys, i tried to compile the module after instaling the 109 patch on fiesty, here is the oputput, i use the lowlatency kernel
Building the vmmon module.

Building for VMware Player 1.0.2 or 1.0.3 or VMware Workstation 5.5.2 or 5.5.3.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /usr/src/linux-headers-2.6.20-15-lowlatency/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-lowlatency'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/task.o
gcc: error trying to exec 'cc1plus': execvp: No such file or directory
make[2]: *** [/tmp/vmware-config1/vmmon-only/common/task.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-lowlatency'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.



help would be greatly appreaciated.
Thanks:guitar:

sudo apt-get install g++

---

### Post by nvrpaul on 2007-04-27
> **duhblow7 said:**
> sudo apt-get install g++
that did it, thanks, i should have thought about that, but i didn't unfourtanately :guitar:

---

### Post by mango.muncher on 2007-05-01
Thanks for this info Teomatto, it worked a treat for my vm reinstall after upgrading to Feisty.

---

### Post by shakma on 2007-05-03
Thanks for the help!  Just trying vmware for the first time, and I thought my recent fiesty update had thwarted me... not so!!!

Peace.

---

### Post by flathampster on 2007-05-25
Brilliant, this was a lifesaver.
It seems they are up to version 110 now.

[http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-any-any-update110.tar.gz](http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-any-any-update110.tar.gz)

---

### Post by clydegoffe on 2007-06-05
flathampster  	Brilliant, this was a lifesaver.
It seems they are up to version 110 now.

[http://platan.vc.cvut.cz/ftp/pub/vmw...date110.tar.gz](http://platan.vc.cvut.cz/ftp/pub/vmw...date110.tar.gz)


-------------------------------------------


Update 110 worked for me.

---

### Post by veloce on 2007-06-06
Or you can install the vmware-server in the commercial repository and never worry about these any-any thingys again!

---

### Post by eaudet on 2007-06-07
> **teomatto said:**
> try this:

download [http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-any-any-update108.tar.gz](http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-any-any-update108.tar.gz)
$ tar zxvf vmware-any-any-update108.tar.gz
$ cd vmware-any-any-update108/
$ sudo ./runme.pl

i had a similiar problem with herd5 and i solved

ciao

THANK YOU! It works!

---

### Post by mattgtries on 2007-08-25
> **teomatto said:**
> try this:

download [http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-any-any-update108.tar.gz](http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-any-any-update108.tar.gz)
$ tar zxvf vmware-any-any-update108.tar.gz
$ cd vmware-any-any-update108/
$ sudo ./runme.pl

i had a similiar problem with herd5 and i solved

ciao

I tried this, except with the vmware-any-any-update113.tar.gz package, and it comes back with this:

mattg@mattg-ubuntu:/media/disk/install/vmware-any-any-update113$ sudo ./runme.pl
sudo: unable to execute ./runme.pl: Permission denied


Any ideas?

---

