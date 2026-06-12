---
title: "Virtualbox problems"
date: 2009-02-04
forum: General Help
---

### Post by FiskFisk33 on 2009-02-04
So i recently installed a fresh copy of interpid, and now Virtualbox 2.1.2 using the deb at their site.

When i try ro start the virtual machine i get
```

VERR_VM_DRIVER_NOT_INSTALLED (rc=-190

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu or Fedora should install the DKMS package at first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.
```

And when i run the command above i get
```
 * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrong

```

 and in the log mentioned above i find
```
Attempting to install using DKMS
  removing old DKMS module vboxdrv version 

Error! Invalid number of parameters passed.
Usage: remove -m <module> -v <module-version> --all
   or: remove -m <module> -v <module-version> -k <kernel-version>

------------------------------
Deleting module version: 2.1.2
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/2.1.2/source ->
                 /usr/src/vboxdrv-2.1.2

DKMS: add Completed.

Error! Your kernel source for kernel 2.6.27-9-server cannot be found at
/lib/modules/2.6.27-9-server/build or /lib/modules/2.6.27-9-server/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:143: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.
```

Any ideas?

---

### Post by jespdj on 2009-02-04
The last part of the error message says what's wrong:
```
Error! Your kernel source for kernel 2.6.27-9-server cannot be found at
/lib/modules/2.6.27-9-server/build or /lib/modules/2.6.27-9-server/source.
```
Install the packages build-essential and linux-headers-generic:
```
sudo apt-get install build-essential linux-headers-generic
```
And try again.

---

### Post by binbash on 2009-02-04
you need to install kernel headers.the version must be same as your current kernel.Sample :

sudo apt-get install linux-headers-2.6.24-23-386

---

### Post by FiskFisk33 on 2009-02-04
Yes thankyou!

---

