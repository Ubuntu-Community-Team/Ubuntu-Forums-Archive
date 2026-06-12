---
title: "ATI 8-10 (Installer/Packer) error"
date: 2008-01-19
forum: Desktop Environments
---

### Post by sgoran on 2008-01-19
I am installing ati-driver-installer-8-01-x86.x86_64.run driver. Using BinaryDriverHowto/ATI method:

sudo apt-get install dkms
./ati-driver-installer-8.443.1-x86.x86_64.run --buildpkg Ubuntu/gutsy
sudo dpkg -i fglrx-kernel-source_<version>.deb
sudo dpkg -i xorg-driver-fglrx_<version>.deb

but on second command i get:

goran@ubuntu:~/Desktop$ ./ati-driver-installer-8-01-x86.x86_64.run --buildpkg Ubuntu/gutsy
Created directory fglrx-install.ij5909
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.452.1.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/gutsy
./packages/Ubuntu/ati-packager.sh: 195: dpkg-architecture: not found
Error: unsupported architecture: 
Removing temporary directory: fglrx-install.ij5909

same thing with ati-driver-installer-8.443.1-x86.x86_64.run

My CPU is x86.

---

### Post by Dragonoff on 2008-01-19
:confused: driver ATI 8.01 installing error :confused:

amd_64 - architecture cpu

~$ sudo ./ati-driver-installer-8-01-x86.x86_64.run --buildpkg Debian/etch
Created directory fglrx-install.ZC8584
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.452.1.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Debian/etch
./packages/Debian/ati-packager.sh: 178: dpkg-architecture: not found
Error: unsupported architecture: 
Removing temporary directory: fglrx-install.ZC8584

:-k

---

### Post by WayneD on 2008-01-21
You need some more packages to be able to run that:

 apt-get install dpkg-dev debhelper

That worked for me.

---

