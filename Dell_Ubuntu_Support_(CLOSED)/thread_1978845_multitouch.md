---
title: "multitouch"
date: 2012-05-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by blackmail on 2012-05-12
I have a dell Inspirion N5110, and i would like to ask how to enable the multitouch on this computer...

Thank you all

---

### Post by gordintoronto on 2012-05-12
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

---

### Post by blackmail on 2012-05-12
Yes, hello and thank you for the prompt response, but sadly I could not install the package mentioned there... an error:

```
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 156349 files and directories currently installed.)
Preparing to replace synaptics-dkms 1.0.0 (using .../synaptics-dkms_1.0.0_all.deb) ...
Unpacking replacement synaptics-dkms ...
Removing old module source...
Setting up synaptics-dkms (1.0.0) ...
Loading new synaptics-1.0.0 DKMS files...

Loading tarball for module: synaptics / version: 1.0.0

Loading /usr/src/synaptics-1.0.0...
Creating /var/lib/dkms/synaptics/1.0.0/source symlink...

DKMS: ldtarball Completed.
Installing prebuilt kernel module binaries (if any)
Building module...

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.38-15-generic-pae -C /lib/modules/2.6.38-15-generic-pae/build SUBDIRS=/var/lib/dkms/synaptics/1.0.0/build modules....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.38-15-generic-pae (i686)
Consult the make.log in the build directory
/var/lib/dkms/synaptics/1.0.0/build/ for more information.
0
0
ERROR: binary package for synaptics: 1.0.0 not found
dpkg: error processing synaptics-dkms (--install):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 synaptics-dkms
```

has occured...

any thoughts on this?

---

### Post by blackmail on 2012-05-15
Ok i have tried reinstalling everything, meaninv that i have switched to ubuntu 12.04 and still no game, I have tried installing a lot of stuff, alps drivers from the launchpad pages, also the synaptics drivers and still nothing, whenever i type:

```
synclient -m 1
```

the response is:

```
Can't access shared memory area. SHMConfig disabled?
Couldn't find synaptics properties. No synaptics driver loaded?

```

---

