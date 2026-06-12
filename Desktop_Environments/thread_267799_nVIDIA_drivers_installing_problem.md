---
title: "nVIDIA drivers installing problem"
date: 2006-09-29
forum: Desktop Environments
---

### Post by Dabrorius on 2006-09-29
Hi
I'm trying to install nVIDIA drviers on ubuntu 6.06 , i'm following this tutorial [http://doc.gwos.org/index.php/Latest_Nvidia_Breezy#METHOD_1](http://doc.gwos.org/index.php/Latest_Nvidia_Breezy#METHOD_1) 
so im stuck on first step of first method ^^

when i execute this command
sudo apt-get install nvidia-glx nvidia-settings linux-restricted-modules-`uname -r`

i get this:

> 
Reading package lists... Done
Building dependency tree... Done
linux-restricted-modules-2.6.15-27-386 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  nvidia-glx: Depends: libglu1-mesa but it is not going to be installedor
                       libglu1
              Conflicts: nvidia-settings but 1.0-3ubuntu7 is to be installed
E: Broken packages




i also tryed "sudo apt-get install libglu1-mesa" but then
> Reading package lists... Done
Building dependency tree... Done
libglu1-mesa is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.


i couldn't google this one out so pls help :)

---

### Post by Beamvr6 on 2006-09-29
Hi Dabrorius,

I recommend installing Automatix and let it install the nVidia drivers for you. It also can install a lot of other usefull stuff for you. It was a great help when I installed Ubuntu for the first time last week.

---

### Post by ajgreeny on 2006-09-29
Did you type *'uname -r'* or actually put in the number when you gave the command, because (I think) you need to put the actual number.  *uname -r* in a terminal will give you the kernel version you are running and the linux-restricted-modules you need is specifically for that kernel.  Try putting in the version numbers you get from *uname -r* and see if it all works better.

---

### Post by Dabrorius on 2006-09-29
> **Beamvr6 said:**
> Hi Dabrorius,

I recommend installing Automatix and let it install the nVidia drivers for you. It also can install a lot of other usefull stuff for you. It was a great help when I installed Ubuntu for the first time last week.

i tried that and averything went fine installation was complete and i had to reboot
then X11 didn't boot it sad it has errors i just used xorg.conf backup and now gnome is back but there is still no new drivers
maybe because i have old graphic card (riva TNT2 32mb :) )

>  	Did you type 'uname -r' or actually put in the number when you gave the command, because (I think) you need to put the actual number. uname -r in a terminal will give you the kernel version you are running and the linux-restricted-modules you need is specifically for that kernel. Try putting in the version numbers you get from uname -r and see if it all works better.

i wasn't sure about that part too but i don't think that is a problem see 3rd line:
"linux-restricted-modules-2.6.15-27-386 is already the newest version."

---

### Post by tseliot on 2006-09-29
> **Dabrorius said:**
> Hi
I'm trying to install nVIDIA drviers on ubuntu 6.06 , i'm following this tutorial [http://doc.gwos.org/index.php/Latest_Nvidia_Breezy#METHOD_1](http://doc.gwos.org/index.php/Latest_Nvidia_Breezy#METHOD_1) 
That guide is for Breezy.

This one is for Dapper:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by Dabrorius on 2006-09-29
problems again :'(
i can't figure out what is he trying to say :(

**sudo apt-get install nvidia-glx **

> Building dependency tree... Done
The following packages will be REMOVED
  nvidia-settings nvidia-xconfig
The following NEW packages will be installed
  nvidia-glx
0 upgraded, 1 newly installed, 2 to remove and 7 not upgraded.
Need to get 0B/4059kB of archives.
After unpacking 11,3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 85936 files and directories currently installed.)
Removing nvidia-settings ...
Removing nvidia-xconfig ...
(Reading database ... 85918 files and directories currently installed.)
Unpacking nvidia-glx (from .../nvidia-glx_1.0.8762+2.6.15.11-5_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx'
dpkg: error processing /var/cache/apt/archives/nvidia-glx_1.0.8762+2.6.15.11-5_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx_1.0.8762+2.6.15.11-5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

