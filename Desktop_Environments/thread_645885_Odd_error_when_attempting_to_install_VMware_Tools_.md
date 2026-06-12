---
title: "Odd error when attempting to install VMware Tools on 7.10..."
date: 2007-12-20
forum: Desktop Environments
---

### Post by sp00ki on 2007-12-20
When attempting to install VMware tools (VMware Workstation 5.5.1) onto Ubuntu 7.10, i run into a problem: vmware-install.pl doesn't seem to recognize my headers.
I'll describe the issue step by step from the beginning:

```
sudo apt-get install linux-headers-`uname -r`
```
(this gives me linux-headers-2.6.22-14-generic)
```
sudo apt-get install build-essential
```
I then go to (from VMware's interface)
VM -> Install VMware Tools...
The "CD" is mounted.
I copy **VMwareTools-5.5.1-19175.tar.gz** to /usr/local/src/
Unpack the tarball and enter the resulting **/usr/local/src/vmware-tools-distrib/** directory and run
```
sudo ./vmware-install.pl
```
Everything seems OK until i get to:
```
What is the location of the directory of C header files that match your running kernel? [/usr/src/linux/include]
```
My headers are located @ **/lib/modules/2.6.22-14-generic/build/include/**
However, when i tell vmware-install.pl to look there, i get:
```
The directory of kernel headers (version @@VMWARE@@ UTS_RELEASE) does not match your running kernel (version 2.6.22-14-generic).  Even if the module were to compile successfully, it would not load into the running kernel.
```
which is partially correct, as uname -r outputs:
```
2.6.22-14-generic
```
when i run:
```
sudo apt-get install linux-headers-2.6.22-14-generic
```
i'm told:
```
linux-headers-2.6.22-14-generic is already the newest version.
```
it seems to me that vmware-install.pl isn't recognizing the headers as valid, though uname -r reports that the running version matches the header files.
does anyone know of a reason that the script wouldn't see the header files as valid?

thanks

---

### Post by AlexzAK on 2007-12-26
[http://ubuntuforums.org/showthread.php?t=623747](http://ubuntuforums.org/showthread.php?t=623747)
May help...

---

### Post by sp00ki on 2007-12-26
I don't speak portuguese, so unfortunately i wasn't able to get much from your link.

It should be noted, though, that i've since installed 6.0.2-- the issue no longer persists.

---

