---
title: "installlation error"
date: 2009-02-11
forum: General Help
---

### Post by geltonas on 2009-02-11
Hi when I try to install any application to my laptop I get this error: 


Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
medibuntu-keyring is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up r5u870-dkms (0.11.1-0ubuntu1~ppa2i) ...
Removing old r5u870-0.11.1 DKMS files...

------------------------------
Deleting module version: 0.11.1
completely from the DKMS tree.
------------------------------
Done.
Loading new r5u870-0.11.1 DKMS files...

Creating symlink /var/lib/dkms/r5u870/0.11.1/source ->
                 /usr/src/r5u870-0.11.1

DKMS: add Completed.
Installing prebuilt kernel module binaries (if any)
Building module...

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.27-11-generic -C /lib/modules/2.6.27-11-generic/build M=/var/lib/dkms/r5u870/0.11.1/build....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.27-11-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/r5u870/0.11.1/build/ for more information.
0
0
dpkg: error processing r5u870-dkms (--configure):
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 r5u870-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)

the r5u870 is the driver for webcam, how could I stop this driver?

---

### Post by ratmandall on 2009-02-11
Try ```
sudo apt-get remove r5u870-dkms
```
It may work, not promising anything tho, heh.

---

### Post by geltonas on 2009-02-11
thanks buddy!

---

