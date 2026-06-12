---
title: "E: couldn't find package linux-restricted-modles"
date: 2005-05-27
forum: Desktop Environments
---

### Post by Curlydave on 2005-05-27
I reformatted and am now using the 32-bit version of utuntu.

I still can't get the ATI drivers installed. I followed the steps in the tutorial, and while most are fine, I get an error at the first one:

> david@computer:~$ sudo apt-get install linux-restricted-modules-</boot/vmlinuz-2.6.10-5-386> xorg-driver-fglrx
Password:
E: Couldn't find package linux-restricted-modules
david@computer:~$

(that's the first step)

Any fixes? Thanks!

(PS: I've installed just about every restricted driver package in existance.)

Oh, and another way of getting it gives me a dif error:
> 
david@computer:~$ sudo apt-get install xorg-driver-fglrx
Password:
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  xorg-driver-fglrx
0 upgraded, 1 newly installed, 0 to remove and 27 not upgraded.
Need to get 0B/3185kB of archives.
After unpacking 10.2MB of additional disk space will be used.

Preconfiguring packages ...
(Reading database ... 73826 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu11_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu11_i386.deb (--unpack):
 trying to overwrite `/usr/X11R6/bin/fgl_glxgears', which is also in package fglrx-6-8-0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu11_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

