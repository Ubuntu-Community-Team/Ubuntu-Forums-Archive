---
title: "Problems with nvidia driver"
date: 2009-04-02
forum: General Help
---

### Post by blood_on_ice on 2009-04-02
Hello

I've tried the following official nvidia-drivers for my geforce GO 7600 graphiccard on my notebook:

NVIDIA-Linux-x86-177.70.33-pkg1
NVIDIA-Linux-x86-180.44-pkg1
NVIDIA-Linux-x86-185.13-pkg0

I use ubuntu 8.10, kernel version:
```
2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux 
```

But none of this drivers work, everytime I get the following error:

nvidia-installer.log
```

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Thu Apr  2 10:02:11 2009
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 180.44.
-> There appears to already be a driver installed on your system (version: 180.
   29).  As part of installing this driver (version: 180.44), the existing driv
   er will be uninstalled.  Are you sure you want to continue? ('no' will abort
   installation) (Answer: Yes)
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.27-11-generic/build'
-> Kernel output path: '/lib/modules/2.6.27-11-generic/build'
ERROR: If you are using a Linux 2.4 kernel, please make sure
       you either have configured kernel sources matching your
       kernel or the correct set of kernel headers installed
       on your system.
       
       If you are using a Linux 2.6 kernel, please make sure
       you have configured kernel sources matching your kernel
       installed on your system. If you specified a separate
       output directory using either the "KBUILD_OUTPUT" or
       the "O" KBUILD parameter, make sure to specify this
       directory with the SYSOUT environment variable or with
       the equivalent nvidia-installer command line option.
       
       Depending on where and how the kernel sources (or the
       kernel headers) were installed, you may need to specify
       their location with the SYSSRC environment variable or
       the equivalent nvidia-installer command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com. 
```

What could be the problem?

Thanks for your help.
Peter

---

### Post by kpkeerthi on 2009-04-02
You may be missing some required packages. See 
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual) for instructions.

---

### Post by blood_on_ice on 2009-04-02
> **kpkeerthi said:**
> You may be missing some required packages. See 
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual) for instructions.

this don't works...

I've tried the following:
- Install the recommend 177 driver with envyng
- Install the driver with System>Administration>Hardware Drivers

With both variants I get the following error at startup:
```
NVIDIA(0): Failed to load the NVIDIA kernel module!

```
And then I have just the 800x600 resolution.

When I try to install the drivers from nvidia I still get the following error:
```

ERROR: If you are using a Linux 2.4 kernel, please make sure
       you either have configured kernel sources matching your
       kernel or the correct set of kernel headers installed
       on your system.
       
       If you are using a Linux 2.6 kernel, please make sure
       you have configured kernel sources matching your kernel
       installed on your system. If you specified a separate
       output directory using either the "KBUILD_OUTPUT" or
       the "O" KBUILD parameter, make sure to specify this
       directory with the SYSOUT environment variable or with
       the equivalent nvidia-installer command line option.
       
       Depending on where and how the kernel sources (or the
       kernel headers) were installed, you may need to specify
       their location with the SYSSRC environment variable or
       the equivalent nvidia-installer command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

I've also tried the steps mentioned here:
[http://nvnews.net/vbulletin/showthread.php?t=72490](http://nvnews.net/vbulletin/showthread.php?t=72490)

Always the same error...

Here's my xconf.org:
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load "glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

Is there any other way to solve my problem?

Thanks for your help.
Peter

---

### Post by norwoods on 2009-04-02
i update to the latest nvidia proprietary prereleases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.44 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using System-->Administration-->Synaptic Package Manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev
for a fresh install, you might also want or need:
jockey-common
jockey-gtk or jockey-kde
nvidia-settings
nvidia-xconfig

---

### Post by blood_on_ice on 2009-04-03
> **norwoods said:**
> i update to the latest nvidia proprietary prereleases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.44 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using System-->Administration-->Synaptic Package Manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev
for a fresh install, you might also want or need:
jockey-common
jockey-gtk or jockey-kde
nvidia-settings
nvidia-xconfig

same error when installing the kernel-source:
```
Processing triggers for man-db ...
Setting up nvidia-180-kernel-source (180.44-0ubuntu1) ...
Removing all DKMS Modules
Done.
Adding Module to DKMS build system
driver version= 180.44
Doing initial module build

Error! Bad return status for module build on kernel: 2.6.27-11-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/nvidia/180.44/build/ for more information.
Installing initial module

Error! Could not locate nvidia.ko for module nvidia in the DKMS tree.
You must run a dkms build for kernel 2.6.27-11-generic (i686) first.
Done.

Setting up nvidia-glx-180 (180.44-0ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
```

make.log:
```
DKMS make.log for nvidia-180.44 for kernel 2.6.27-11-generic (i686)
Fri Apr  3 08:49:46 CEST 2009
If you are using a Linux 2.4 kernel, please make sure
you either have configured kernel sources matching your
kernel or the correct set of kernel headers installed
on your system.

If you are using a Linux 2.6 kernel, please make sure
you have configured kernel sources matching your kernel
installed on your system. If you specified a separate
output directory using either the "KBUILD_OUTPUT" or
the "O" KBUILD parameter, make sure to specify this
directory with the SYSOUT environment variable or with
the equivalent nvidia-installer command line option.

Depending on where and how the kernel sources (or the
kernel headers) were installed, you may need to specify
their location with the SYSSRC environment variable or
the equivalent nvidia-installer command line option.

*** Unable to determine the target kernel version. ***

make: *** [select_makefile] Error 1
```


??

Peter

---

### Post by stargate2500 on 2009-04-03
Did you find a solution, is there any..

---

### Post by norwoods on 2009-04-03
try running the following and then reinstall.
sudo apt-get install build-essential linux-headers-`uname -r`

---

### Post by norwoods on 2009-04-03
Ubuntu Forums from stargate2500 

>>I have a couple of ?s about it.
>>Did ya'll mark his post fixed or did he resolve the problem? 
i did not mark his post fixed and i do not know.
>>What kind of card do you have?
9600gt
>>Every time someone post that type of problem, I take out my 
>>card and replace it with my newer card nvidia gforce4 
>>mx 4000 and try it. Nothing has fixed it. So I'm running 
>>a tnt2 nvidia card with no 3d resolution runs great but no 3d >>support for it. I know it is nvidia problem, but ya'll have 
>>more answers that ya'll give. Heres the post from last night. >>Let me have some feed back. Thank you...
you apparently need to update from 71.86.09 for a tnt2 to 96.43.11 for a geforce4.  do the nvidia driver installers envygt or envy do this for you?
from [http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606)

Current releases
Current official release: 180.44 (x86 / x86_64)
Current beta release: 185.13

Legacy releases for GeForce 5 series GPUs
Current official release: 173.14.18 (x86 / x86_64)

Legacy releases for GeForce 2 through GeForce 4 series GPUs
Current official release: 96.43.11 (x86 / x86_64)

Legacy releases for Riva TNT, TNT2, GeForce, and some GeForce 2 GPUs
Current official release: 71.86.09 (x86 / x86_64)

Please see Appendix A of the README to determine which driver you need for your GPU.

---

### Post by blood_on_ice on 2009-04-05
I've ended up in reinstalling ubuntu...now I'm using the recommended 177 nvidia driver installed with System>Administration>Hardware Drivers and all works fine...conclusion: hands away from the official nvidia-driver!

Greetings
Peter

---

### Post by norwoods on 2009-04-05
the nvidia 185.13 driver is now in the intrepid main repository.

---

