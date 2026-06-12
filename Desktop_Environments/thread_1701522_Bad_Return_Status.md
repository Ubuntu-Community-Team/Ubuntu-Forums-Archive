---
title: "Bad Return Status"
date: 2011-03-06
forum: Desktop Environments
---

### Post by nikhilneela on 2011-03-06
Hi everyone, I recently installed ubuntu 10.10 and wanted gnome3 for it. I found this reference for installing gnome3.[http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html](http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html). When i run the script present in the installation procedure, the script said to install libusb-1.0-0-dev 
. When i used sudo apt-get install libusb-1.0-0-dev i get the following error
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libusb-1.0-0-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 236 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Removing old bcmwl-5.60.48.36+bdcom DKMS files...

------------------------------
Deleting module version: 5.60.48.36+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 2.6.35-22-generic
Building for architecture i686
Building initial module for 2.6.35-22-generic

Error! Bad return status for module build on kernel: 2.6.35-22-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/ for more information.
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module>
    report.write(open(apport.fileutils.make_report_path(report), 'w'))
IOError: [Errno 2] No such file or directory: '/var/crash/bcmwl-kernel-source.0.crash'
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)


```
Please help me

---

