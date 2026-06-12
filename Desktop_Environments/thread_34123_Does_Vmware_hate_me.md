---
title: "Does Vmware hate me?"
date: 2005-05-13
forum: Desktop Environments
---

### Post by tseliot on 2005-05-13
Hi, when I try to install Vmware version 5.0.0-13124 (the RPM from the official website) with Kpackage (or with dpkg) here's what it says:

<re-workstation-5.0.0-13124.i386.rpm';echo RESULT=$?
error: failed dependencies:
 /bin/sh   is needed by VMwareWorkstation-5.0.0-13124
RESULT=1

No matter what kernel header I install.

Any ideas?

---

### Post by StacyWebb on 2005-05-13
You did convert the rpm to a deb first with alien right?

---

### Post by tseliot on 2005-05-14
I've done as you said and I got to install it.

Now I enter "vmware" in the terminal and this is what I get:

/usr/bin/vmware: line 85: /etc/vmware/locations: No such file or directory
/usr/bin/vmware: line 183: /lib/wrapper-gtk24.sh: No such file or directory
/usr/bin/vmware: line 183: exec: /lib/wrapper-gtk24.sh: cannot execute: No such file or directory

What's wrong?

---

### Post by tseliot on 2005-05-14
I've found the answer here:

[http://www.ubuntuforums.org/showthread.php?t=30232&highlight=vmware](http://www.ubuntuforums.org/showthread.php?t=30232&highlight=vmware)

Sorry for making you lose your time.

bye

---

### Post by tseliot on 2005-05-14
this is what I get when I try to configure it:

Configuring fallback GTK+ 2.4 libraries.

***
* Updating MIME database in /usr/share/mime...
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

Your kernel was built with "gcc" version "3.0.4", while you are trying to use
"/usr/bin/gcc" version "3.3.5". This configuration is not recommended and VMware
Workstation may crash if you'll continue. Please try to use exactly same
compiler as one used for building your kernel. Do you want to go with compiler
"/usr/bin/gcc" version "3.3.5" anyway? [no] yes

What is the location of the directory of C header files that match your running
kernel?
[/lib/modules/2.6.8.1-03-NeTraverse-i686-UP-4GB/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmmon-only'
make -C /lib/modules/2.6.8.1-03-NeTraverse-i686-UP-4GB/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/lib/modules/2.6.8.1-03-NeTraverse-i686-UP-4GB/build'
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config2/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config2/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST
  CC      /tmp/vmware-config2/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config2/vmmon-only/vmmon.ko
make[1]: Leaving directory `/lib/modules/2.6.8.1-03-NeTraverse-i686-UP-4GB/build'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to make a vmmon module that can be loaded in the running kernel:
insmod: error inserting '/tmp/vmware-config2/vmmon.o': -1 Invalid module format
There is probably a slight difference in the kernel configuration between the
set of C header files you specified and your running kernel.  You may want to
rebuild a kernel based on that directory, or specify another directory.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

What can I do? ](*,)

---

### Post by rattaro on 2005-05-14
I think you are looking in the wrong folder for the kernel headers.  Look in:

/usr/src/linux-headers-2.6.10-5-386/include,   If you have this file.

depending upon your computer configuration, the "linux-headers" folder may have another name, but the rest should be in this location.

---

### Post by mrbass on 2005-05-15
Install VMWare 5.0
**uname -a**
Linux hostname 2.6.10-5-386
**sudo apt-cache search headers 2.6.10-5-386**
linux-headers-2.6.10-5-386 - Linux kernel headers 2.6.10 on 386
[b]sudo apt-get install linux-headers-2.6.10-5-386
sudo apt-get install gcc[/b]
Now your ready to install VMWare with the script

---

### Post by tseliot on 2005-05-15
Thanks guys. I just had to restart my computer with the right (default) linux kernel instead of that provided with  Win4lin. 
Now it works

---

