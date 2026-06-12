---
title: "apt-get problems? libGL.so.1.2 issue"
date: 2005-08-08
forum: Desktop Environments
---

### Post by holr on 2005-08-08
Hi,
  Whenever I try to do anything with apt-get now, its telling me i have dependancy issues. Im getting the following after a sudo apt-get -f install
huw@ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  xlibmesa-gl
The following NEW packages will be installed:
  xlibmesa-gl
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
113 not fully installed or removed.
Need to get 0B/308kB of archives.
After unpacking 762kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  xlibmesa-gl
Install these packages without verification [y/N]? y

Preconfiguring packages ...
(Reading database ... 121656 files and directories currently installed.)
Unpacking xlibmesa-gl (from .../xlibmesa-gl_6.8.2-10_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/xlibmesa-gl_6.8.2-10_i386.deb (--unpack):
 trying to overwrite `/usr/X11R6/lib/libGL.so.1.2', which is also in package fglrx-6-8-0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/xlibmesa-gl_6.8.2-10_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
huw@ubuntu:~$

I *did* manage to get atis fglrx driver (8.14.13) installed for better performance with doom 3, im guessing that whatever I did with that is the root of this issue? What do i do?!? I dont really want to get rid of the latest ati drivers because there is a big performance boost over the ones with synaptic...

thanks!

---

### Post by holr on 2005-08-09
Anyone any ideas what I can do? Dont really want to have to reinstall ubuntu again... just when I thought I had it working nicely!

---

### Post by holr on 2005-08-10
[QUOTE=holr]Anyone any ideas what I can do? Dont really want to have to reinstall ubuntu again... just when I thought I had it working nicely![/QUOTE]
 ok, managed to solve the problem. Did a dpkg -l > list.txt to see what the package was called (fglrx-6-8-0 i think), then did a sudo dpkg -r fglrx-6-8-0 to remove the package from the system. sudo apt-get upgrade now worked. Downloaded the ati installer script (the *.run file) and ran that with sudo sh ati-blah-blah.run. Restarted X with alt-ctrl-backspace and hey presto! still have doom 3 running nice! And no more complaints from apt-get!

---

