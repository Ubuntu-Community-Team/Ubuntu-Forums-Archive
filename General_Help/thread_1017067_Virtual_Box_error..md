---
title: "Virtual Box error."
date: 2008-12-20
forum: General Help
---

### Post by miked860 on 2008-12-20
VERR_VM_DRIVER_NOT_INSTALLED (rc=-1908

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu or Fedora should install the DKMS package at first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

Have no idea what it means.

---

### Post by miked860 on 2008-12-20
I have also executed the command and it does nothing.

---

### Post by miked860 on 2008-12-20
Error! Your kernel source for kernel 2.6.27-9-generic cannot be found at
/lib/modules/2.6.27-9-generic/build or /lib/modules/2.6.27-9-generic/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:142: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.

I get that error when I try to run that command

---

### Post by miked860 on 2008-12-20
Can someone please help me?

---

