---
title: "Psmouse problem revived."
date: 2008-11-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Sesetamhet on 2008-11-07
I am running a Dell Inspiron 1420N, and the trackpad does not allow vertical scrolling. I believe that this problem existed in Fiesty(and has been discussed on other forums), and was solved by the release of the psmouse-dkms package:[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Scrolling_feature_on_touchpad_does_not_work]("http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Scrolling_feature_on_touchpad_does_not_work")

However, this problem has resurfaced in 8.10, at least for my machine, and now the fix no longer works completely. The package returns errors upon installation. (Simply, installation incomplete, no more info given upon checking terminal output.) Now, the scrolling will work, but only after I manually reload the psmouse-dkms module after bootup. Furthermore, the package returns the following error whenever aptitude is used for any purpose.:
```

carson@yggdrasil:~$ sudo aptitude install gnuplot
[sudo] password for carson: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following partially installed packages will be configured:
  psmouse-dkms 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up psmouse-dkms (2.6.20-16.29-1) ...
Removing old psmouse-2.6.20-16.29-1 DKMS files...

-------- Uninstall Beginning --------
Module:  psmouse
Version: 2.6.20-16.29-1
Kernel:  2.6.20-16-generic (i686)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod....(bad exit status: 1)

DKMS: uninstall Completed.

------------------------------
Deleting module version: 2.6.20-16.29-1
completely from the DKMS tree.
------------------------------
Done.
Loading new psmouse-2.6.20-16.29-1 DKMS files...

Error! Cannot locate /usr/src/psmouse-2.6.20-16.29-1.dkms.tar.gz.
File does not exist.
dpkg: error processing psmouse-dkms (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 psmouse-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up psmouse-dkms (2.6.20-16.29-1) ...
Loading new psmouse-2.6.20-16.29-1 DKMS files...

Error! Cannot locate /usr/src/psmouse-2.6.20-16.29-1.dkms.tar.gz.
File does not exist.
dpkg: error processing psmouse-dkms (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 psmouse-dkms
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

carson@yggdrasil:~$ 

```

This is a very annoying thing to see every time I use my package manager, and it is also trouble to reload the kernel module every time I use my computer. Any help would be appreciated!

---

