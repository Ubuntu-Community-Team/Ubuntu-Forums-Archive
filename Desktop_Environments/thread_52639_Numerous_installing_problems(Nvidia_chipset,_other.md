---
title: "Numerous installing problems(Nvidia chipset, other apps)"
date: 2005-07-28
forum: Desktop Environments
---

### Post by Tinuz on 2005-07-28
I have a few installation problems on my new Kubuntu64 system. 

1. I have tried to install G++, a development tool recommended by the scientific programmer at my university. It comes standard in the package manager so the 'true' installing isn't much of a problem. I does no show up on my system though and i cannot find it anywhere. I have tried to input some of the most logical names in the 'Run command'-console, but to no avail. 

2. I have tried to install the Nforce drivers(i have an A8N-SLI) but installing them gives me errors. First, the drivers require the linux source headers(or something of that nature, kernel sources) and after searching through apt-get i have found and installed them. Now it gives my an unspecified error with a pointer to a log file which(unfortunatly) tells me little more then the errors printed on the screen, theres a dump of it below this post. 

Besides all this, the konqeuror crashes very often. Not much of a problem, but it annoys me. Perhaps some sort of bug, but it shows very little of a pattern.
Also, does anyone know a good tutorial to the bash scripting. I admit not have looked myself(not top of the list at this moment), but if someone knows a gooed tutorial, i would like to hear it. 
Thanks in advance

---

### Post by Tinuz on 2005-07-28
The log file, found in var/log/Nvidia.....log.

nforce-installer log file '/var/log/nvidia-nforce-installer.log'
creation time: Thu Jul 28 12:47:21 2005

option status:
  license pre-accepted      : false
  expert                    : false
  uninstall                 : false
  driver info               : false
  no precompiled interface  : false
  no ncurses color          : false
  no questions              : false
  silent                    : false
  Installer install prefix  : /usr
  kernel source path        : (not specified)
  net kernel install path   : (not specified)
  audio kernel install path : (not specified)
  proc mount point          : /proc
  ui                        : (not specified)
  tmpdir                    : /tmp

Using: nvidia-installer ncurses user interface
-> Found package NVIDIA audio driver for Linux-x86_64
-> Found package NVIDIA network driver for Linux-x86_64
-> Please select packages for installation:
   Selections:
   NVIDIA audio driver for Linux-x86_64 (1.0-2)
   NVIDIA network driver for Linux-x86_64 (1.0-11)
-> Starting install of NVIDIA audio driver for Linux-x86_64
-> Checking for loaded module nvsound
-> Checking for loaded module nvaudio
-> License accepted.
-> Skipping check for conflicting rpms.
-> /proc/version is Linux version 2.6.10-5-amd64-generic (buildd@yellow) (gcc
   version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Fri Jun 24 16:54:18 UTC 2005
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Kernel source path: '/lib/modules/2.6.10-5-amd64-generic/build'
-> Kernel output path: '/lib/modules/2.6.10-5-amd64-generic/build'
-> Performing cc_version_check with CC="cc".
-> gcc-version-check failed:
   
   ./nvsound/main/conftest.sh: line 9: cc: command not found
   Could not compile gcc-version-check.c
   
   If you know what you are doing and want to ignore the gcc version check, sel
   ect "No" to continue installation.  Otherwise, select "Yes" to abort install
   ation, set the CC environment variable to the name of the compiler used to c
   ompile your kernel, and restart installation.  Abort now? (Answer: No)
ERROR: ./nvsound/main/conftest.sh: line 9: cc: command not found
       
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
       the appropriate nvidia-installer command line option.
ERROR: Installation of the audio driver has failed.  Please see the file
       '/var/log/nvidia-nforce-installer.log' for details.  You may find
       suggestions on  fixing installation problems in the README available on
       the Linux driver download page at [www.nvidia.com](www.nvidia.com).
-> Starting install of NVIDIA network driver for Linux-x86_64
-> Checking for loaded module nvnet
-> Checking for loaded module forcedeth
-> Trying to remove loaded module forcedeth
-> License accepted.
-> Skipping check for conflicting rpms.
-> /proc/version is Linux version 2.6.10-5-amd64-generic (buildd@yellow) (gcc
   version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Fri Jun 24 16:54:18 UTC 2005
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Using the kernel source path '/lib/modules/2.6.10-5-amd64-generic/build' as
   specified by the '--kernel-source-path' commandline option.
-> Kernel source path: '/lib/modules/2.6.10-5-amd64-generic/build'
-> Using the kernel output path '/lib/modules/2.6.10-5-amd64-generic/build' as
   specified by the '--kernel-output-path' commandline option.
-> Kernel output path: '/lib/modules/2.6.10-5-amd64-generic/build'
-> Performing cc_version_check with CC="cc".
ERROR: ./nvnet/conftest.sh: line 9: cc: command not found
       
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
       the appropriate nvidia-installer command line option.
ERROR: Installation of the network driver has failed.  Please see the file
       '/var/log/nvidia-nforce-installer.log' for details.  You may find
       suggestions on  fixing installation problems in the README available on
       the Linux driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by ykpaiha on 2005-07-28
I guess you didn't look very deeply in the howto the prob you mention and I can see can be easly tuned out installing only proper pacjkages.....

I guess the first help you can get is : YOU

Lol of course 

Here is a clue =>
install the meta package buid essential (you 'll find it in synaptic if enabled the right depos.


the rest is here
[http://www.frankandjacq.com/ubuntuguide/5.04/index.html](http://www.frankandjacq.com/ubuntuguide/5.04/index.html)
or here
[http://www.ubuntuforums.org/showthread.php?t=31094](http://www.ubuntuforums.org/showthread.php?t=31094)

Welcome in the freeworld

---

