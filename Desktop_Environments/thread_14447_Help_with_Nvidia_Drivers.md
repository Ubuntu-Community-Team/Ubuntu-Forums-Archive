---
title: "Help with Nvidia Drivers"
date: 2005-02-07
forum: Desktop Environments
---

### Post by Y3k on 2005-02-07
I tried to install Nvidia drivers for my GEFORCE 6800 GT, i closed graphic mode with killall gdm, i launched the driver installation in this way (as explained on readme of nvidia drivers): sh NVIDIA-Linux(etc etc etc).run


the installation program loaded, but after it gives me this error message:

[color=red][b]
ERROR: Unable to find the kernel source tree for the currently running kernel. Please make sure you have installed the kernel source files for your kernel, on red hat linux system for example, be sure you have the "kernel source rpm installed" you may specity the kernel source path with the --kernel-source-patch commandline option.[/color][/b]

what should i do now? :?:  :?:  :?:

---

### Post by Y3k on 2005-02-07
help pls...

---

### Post by jdodson on 2005-02-07
[QUOTE=Y3k]I tried to install Nvidia drivers for my GEFORCE 6800 GT, i closed graphic mode with killall gdm, i launched the driver installation in this way (as explained on readme of nvidia drivers): sh NVIDIA-Linux(etc etc etc).run


the installation program loaded, but after it gives me this error message:

[color=red][b]
ERROR: Unable to find the kernel source tree for the currently running kernel. Please make sure you have installed the kernel source files for your kernel, on red hat linux system for example, be sure you have the "kernel source rpm installed" you may specity the kernel source path with the --kernel-source-patch commandline option.[/color][/b]

what should i do now? :?:  :?:  :?:[/QUOTE]

try installing the drivers using this guide : [http://www.ubuntuguide.org](http://www.ubuntuguide.org) - it makes installing the drivers as simple as pasting in 3 commands to the command line.

btw, sometimes it takes people hours to respond.  waiting 30 minutes is not a big deal as our user base is worldwide and does not operate on the same timezone.

---

### Post by rosslaird on 2005-02-07
This is just a commiseration post.
I have had this exact problem, and it was one of the many things that drove me batty about the nvidia drivers. The suggested fix above should work fine.
Nvidia is weird: they do have better support for Linux, but so many people seem to have trouble with nvidia setup.

On my recent install of ubuntu, I did this (I don't know if this will work for you):

apt-get install nvidia-glx
apt-get install nvidia-settings
nvidia-glx-config enable


This worked perfectly, and for the first time my nvidia setup went without a hitch. (I have spent hours and hours in Xandros and Debian and Gentoo on nvidia setup issues).
Good for Ubuntu to make it so workable.

---

### Post by friez on 2005-02-07
if you want to install the nvidia-driver from there website you must have the kernel sources install and have a symlink for it```
ln -s /usr/src/MY_KERNEL_SOURCE /usr/src/linux
``` the nvidia driver are built from the kernel sources so it's different for each kernel

---

