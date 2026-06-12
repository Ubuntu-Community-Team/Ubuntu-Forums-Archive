---
title: "Unable to install NVIDIA 180.16 driver"
date: 2008-12-20
forum: General Help
---

### Post by obsrv on 2008-12-20
Unable to install 180.16 driver from nvidia. This is what I get:

```
obsrv@pirate:~$ cat /var/log/nvidia-installer.log 
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sun Dec 21 05:41:01 2008
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
  no cc version check     : true
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  compat32 install chroot : (not specified)
  compat32 install prefix : (not specified)
  compat32 install libdir : (not specified)
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
-> Installing NVIDIA driver version 177.82.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: No)
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Performing CC sanity check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.28-3-generic/build'
-> Kernel output path: '/lib/modules/2.6.28-3-generic/build'
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
obsrv@pirate:~$ 
```

I followed instructions from help.ubuntu.com

---

### Post by stderr on 2008-12-20
Since it's trying to compile a kernel module/header/something, it should probably need the kernel source code. I *think* this should do the job:

```
sudo apt-get install linux-source
```

---

### Post by obsrv on 2008-12-20
I have it and its symlinked and oldconfig made.

---

### Post by stderr on 2008-12-20
Did you try using a command line switch to specify their correct location?

It's just '/lib/modules/2.6.28-3-generic/build' looks wrong...

I don't know which method you acquired it with, but if it's from the ubuntu servers as above it seems to dump it as a .tgz to /usr/src. The NVIDIA installer says it looks under /lib/modules/.../build and /usr/src/linux, so try extracting the sources to /usr/src/linux and running with --kernel-source-path=/usr/src/linux. That should rule out anything wrong under the /lib/modules/... dir

But if you've already got the sources correctly symlinked under /lib/modules/... then I don't know.

---

