---
title: "Nvidia driver will not install properly"
date: 2005-11-13
forum: Gaming &amp; Leisure
---

### Post by just1m on 2005-11-13
Loaded Ubuntu (newbie to Linux) yesterday in a Dell P4 2.6 GHZ with a Nvidia FX5200. I can't get this computer to run OpenGL. Help.

---

### Post by just1m on 2005-11-13
Ubuntu 5.10

---

### Post by 23meg on 2005-11-13
Did you follow the instructions given in [this thread]("http://www.ubuntuforums.org/showthread.php?t=75074")?

---

### Post by just1m on 2005-11-13
yes unless there is something that I tried incorrectly

---

### Post by 23meg on 2005-11-13
Please give more details; what exactly is going wrong? Did the installer give you any errors?

---

### Post by just1m on 2005-11-13
I've tried all the options. Option one just gets me to failed to start the x server . . .ect. Option three does the same. Option two gets me to the Nvidia install program and the program tells me that cc tool is not in Your path

---

### Post by professor_chaos on 2005-11-13
I'm not following all of what your saying, but to install the official drivers from nvidia and you get a problem regarding cc. First install gcc-3.4 (i think this is right) and then set the variable "CC" equal to gcc-3.4. You do this from the command line right before you start the nvidia driver setup, by "export CC=gcc3.4". This will allow the setup to use gcc-3.4 as your compiler. Before you do all of this, make sure you uninstall all of the packages on your system that have the word nvidia in it.
Good luk

---

### Post by just1m on 2005-11-13
I did that. When I try to set a manual link to the CC (as stated in problems section) it tells me that link already exists

---

### Post by 23meg on 2005-11-14
[QUOTE=professor_chaos] by "export CC=gcc3.4". This will allow the setup to use gcc-3.4 as your compiler. [/QUOTE]

That should be gcc-3.4. Try it this way: ```
CC=gcc-3.4
export CC
```

Also make sure you have gcc, gcc-3.4 and gcc-3.4-base installed.

---

### Post by just1m on 2005-11-14
Anyone still here? I just tried option one again. But the Nvidia configuration tool doesn't have anything in it

---

### Post by 23meg on 2005-11-14
Please post the contents of your /var/log/nvidia-installer.log file.

---

### Post by just1m on 2005-11-14
how do i get the info

---

### Post by 23meg on 2005-11-14
```
gedit /var/log/nvidia-installer.log
```

and copy and paste here in quote tags.

---

### Post by just1m on 2005-11-14
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sun Nov 13 20:19:46 2005

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
ERROR: Unable to find the development tool `cc` in your path; please make sure
       that you have the package 'gcc' installed.  If gcc is installed on your
       system, then please check that `cc` is in your PATH.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by 23meg on 2005-11-14
```
sudo apt-get install gcc gcc-3.4 gcc-3.4-base
```

---

### Post by just1m on 2005-11-14
When I put in the code you ask I get

Reading package lists... Done
Building dependency tree... Done
gcc is already the newest version.
gcc-3.4 is already the newest version.
gcc-3.4-base is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by 23meg on 2005-11-14
Try this and run the installer again:```
sudo ln -s /usr/bin/gcc /usr/bin/cc
```

---

### Post by just1m on 2005-11-16
still didn't work. Any other ideas?

---

