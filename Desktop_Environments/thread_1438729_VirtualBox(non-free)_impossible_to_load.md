---
title: "VirtualBox(non-free) impossible to load"
date: 2010-03-25
forum: Desktop Environments
---

### Post by lorap1 on 2010-03-25
Impossible to load VB with Windows 7 (or Windows XP) as Guest Host ; it says:
execute "/etc/init.d/vboxdrv setup".
So did I, as root, enven with gksudo.
But no result came up.
- linux headers already installed (2.6.31-20-generic-pae)
-/var/log/vbox-install.log says
```
** Compiling vboxdrv
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxdrv/3.1.4/source ->
                 /usr/src/vboxdrv-3.1.4

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area.....
su nobody -c "make KERNELRELEASE=2.6.31-20-generic-pae -C /lib/modules/2.6.31-20-generic-pae/build M=/var/lib/dkms/vboxdrv/3.1.4/build"...............................................................................

Running the post_build script:
cleaning build area....

DKMS: build Completed.

vboxdrv.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.31-20-generic-pae/updates/dkms/

depmod..................

DKMS: install Completed.
** Compiling vboxnetflt
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxnetflt/3.1.4/source ->
                 /usr/src/vboxnetflt-3.1.4

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Running the pre_build script:

Building module:
cleaning build area....
su nobody -c "make KERNELRELEASE=2.6.31-20-generic-pae -C /lib/modules/2.6.31-20-generic-pae/build M=/var/lib/dkms/vboxnetflt/3.1.4/build"............
cleaning build area....

DKMS: build Completed.

vboxnetflt.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.31-20-generic-pae/updates/dkms/

depmod..........

DKMS: install Completed.
** Compiling vboxnetadp
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxnetadp/3.1.4/source ->
                 /usr/src/vboxnetadp-3.1.4

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Running the pre_build script:

Building module:
cleaning build area....
su nobody -c "make KERNELRELEASE=2.6.31-20-generic-pae -C /lib/modules/2.6.31-20-generic-pae/build M=/var/lib/dkms/vboxnetadp/3.1.4/build".........
cleaning build area....

DKMS: build Completed.

vboxnetadp.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.31-20-generic-pae/updates/dkms/

depmod.......

DKMS: install Completed. 
```Finally : ```
  p, li { white-space: pre-wrap; }     Code de résultat : 
  NS_ERROR_FAILURE (0x80004005)
   Composant :
  Machine
   Interface : 
  IMachine {99404f50-dd10-40d3-889b-dd2f79f1e95e}

```If somebody knows how to trick it out...:)

---

