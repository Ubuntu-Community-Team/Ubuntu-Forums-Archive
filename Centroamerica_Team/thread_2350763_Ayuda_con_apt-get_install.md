---
title: "Ayuda con apt-get install"
date: 2017-01-27
forum: Centroamerica Team
---

### Post by jacocalde on 2017-01-27
Cuando trato de instalar un paquete, me dice que hay un error en el sistema y que corra el siguiente comando:

```
sudo apt-get -f install
```

Este es el output:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  libc6 libc6:i386
Suggested packages:
  glibc-doc glibc-doc:i386 locales:i386
The following packages will be upgraded:
  libc6 libc6:i386
2 upgraded, 0 newly installed, 0 to remove and 154 not upgraded.
2 not fully installed or removed.
Need to get 0 B/4 856 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Preconfiguring packages ...
(Reading database ... 298425 files and directories currently installed.)
Preparing to unpack .../libc6_2.23-0ubuntu5_amd64.deb ...
De-configuring libc6:i386 (2.23-0ubuntu4) ...


LD_LIBRARY_PATH contains the traditional /lib directory,
but not the multiarch directory /lib/x86_64-linux-gnu.
It is not safe to upgrade the C library in this situation;
please remove the /lib/directory from LD_LIBRARY_PATH and
try again.


dpkg: error processing archive /var/cache/apt/archives/libc6_2.23-0ubuntu5_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Preparing to unpack .../libc6_2.23-0ubuntu5_i386.deb ...
De-configuring libc6:amd64 (2.23-0ubuntu4) ...


LD_LIBRARY_PATH contains the traditional /lib directory,
but not the multiarch directory /lib/i386-linux-gnu.
It is not safe to upgrade the C library in this situation;
please remove the /lib/directory from LD_LIBRARY_PATH and
try again.


dpkg: error processing archive /var/cache/apt/archives/libc6_2.23-0ubuntu5_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.23-0ubuntu5_amd64.deb
 /var/cache/apt/archives/libc6_2.23-0ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)





Alguien sabe como arreglarlo?

---

