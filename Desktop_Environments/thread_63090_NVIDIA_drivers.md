---
title: "NVIDIA drivers"
date: 2005-09-06
forum: Desktop Environments
---

### Post by HolyShnikes on 2005-09-06
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Mon Sep  5 17:52:19 2005

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: false
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/X11R6
  OpenGL install prefix   : /usr
  compat32 install prefix : (not specified)
  installer install prefix: /usr
  utility install prefix  : /usr
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel; on Red Hat Linux systems, for example, be sure you have the
       'kernel-source' rpm installed.  If you know the correct kernel source
       files are installed, you may specify the kernel source path with the
       '--kernel-source-path' commandline option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).


what can I do please?  and dont just say "read this" and post a link.  cause I have tried just about every how to on the site.  I have done so many things to get this to work.  I got it to work once, but that was after I had junked up my linux drive and I wanted to reformatt.  After I reformatted I couldnt get it to work.  I spent 5 hours today trying to get it to work again, installing all kinds of things that "could" make it work and it did nothing but screw it up.  So what did I do?  I reformatted again and started fresh. so could somone just please, and I mean PLEASE just let me know how to do this so I dont have to smash my head against the wall  ](*,)

---

### Post by ltmon on 2005-09-06
Hi,

Do you actually need to use the nvidia driver installer?  I ask this becase (just in case you weren't aware) the nvidia drivers are installable via Synaptic, which is much easier.  See [https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia) (oops... I posted a link ;) ).

If you do _really_ need to use the nvidia installer (i.e. if you need the absolute latest, greatest drivers is the only reason) your problem seems to be that you are missing the source for your kernel (which is needed to install the driver this way).

Install it by:

> sudo apt-get install linux-source

and try again.

Cheers,

L.

---

### Post by HolyShnikes on 2005-09-07
I will try that, thanks.  And yes I do need the drivers installed this way.  When I tried using synatic (nvidia-glx, etc.) I get a messed up screen and when I change the settings back it boots up into the console....so then I have to change my divice to nvidia again so it will load up.  Its just a pain in the butt.  But I will try what you suggested and let you know if it works or not

::EDIT::  I just tried and I got this.

```
Reading package lists... Done
Building dependency tree... Done
Package linux-source is a virtual package provided by:
  linux-source-2.6.10 2.6.10-34.4
  linux-source-2.6.11 2.6.11-0.2
You should explicitly select one to install.
E: Package linux-source has no installation candidate
``` 

Which should I do???

---

### Post by tseliot on 2005-09-07
sudo apt-get install linux-tree

or install "linux tree" in synaptic

get the same version as your current kernel (type "uname -r" to see which kernel is yours)

---

