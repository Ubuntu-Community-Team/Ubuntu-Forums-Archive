---
title: "To install new ati driver easy"
date: 2008-12-20
forum: General Help
---

### Post by sdowney717 on 2008-12-20
how to install new ati driver
download from AMD
generate the package, for me it is 8.10, for others use 8.04

sudo ./ati-driver-installer-8-12-x86.x86_64.run --buildpkg Ubuntu/8.10

then install all the new packages
sudo dpkg -i *.deb

```


scott@scott-desktop:~/ati$ sudo ./ati-driver-installer-8-12-x86.x86_64.run --buildpkg Ubuntu/8.10
Created directory fglrx-install.x11360
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.561............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/8.10
Package /home/scott/ati/xorg-driver-fglrx_8.561-0ubuntu1_i386.deb has been successfully generated
Package /home/scott/ati/xorg-driver-fglrx-dev_8.561-0ubuntu1_i386.deb has been successfully generated
Package /home/scott/ati/fglrx-kernel-source_8.561-0ubuntu1_i386.deb has been successfully generated
Package /home/scott/ati/fglrx-amdcccle_8.561-0ubuntu1_i386.deb has been successfully generated
Package /home/scott/ati/fglrx-modaliases_8.561-0ubuntu1_i386.deb has been successfully generated
Package /home/scott/ati/libamdxvba1_8.561-0ubuntu1_i386.deb has been successfully generated
Removing temporary directory: fglrx-install.x11360
scott@scott-desktop:~/ati$ sudo dpkg -i *.deb
(Reading database ... 245481 files and directories currently installed.)
Preparing to replace fglrx-amdcccle 2:8.543-0ubuntu4 (using fglrx-amdcccle_8.561-0ubuntu1_i386.deb) ...
Unpacking replacement fglrx-amdcccle ...
Preparing to replace fglrx-kernel-source 2:8.543-0ubuntu4 (using fglrx-kernel-source_8.561-0ubuntu1_i386.deb) ...
Removing all DKMS Modules
rpmdb: lock_downgrade: Lock is no longer valid
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - Invalid argument (22)
error: cannot open Packages database in /var/lib/rpm
rpmdb: lock_downgrade: Lock is no longer valid
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - Invalid argument (22)
error: cannot open Packages database in /var/lib/rpm
rpmdb: lock_downgrade: Lock is no longer valid
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - Invalid argument (22)
error: cannot open Packages database in /var/lib/rpm
rpmdb: lock_downgrade: Lock is no longer valid
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - Invalid argument (22)
error: cannot open Packages database in /var/lib/rpm
rpmdb: lock_downgrade: Lock is no longer valid
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - Invalid argument (22)
error: cannot open Packages database in /var/lib/rpm
rpmdb: lock_downgrade: Lock is no longer valid
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - Invalid argument (22)
error: cannot open Packages database in /var/lib/rpm
Done.
Unpacking replacement fglrx-kernel-source ...
Preparing to replace fglrx-modaliases 2:8.543-0ubuntu4 (using fglrx-modaliases_8.561-0ubuntu1_i386.deb) ...
Unpacking replacement fglrx-modaliases ...
Preparing to replace libamdxvba1 2:8.543-0ubuntu4 (using libamdxvba1_8.561-0ubuntu1_i386.deb) ...
Unpacking replacement libamdxvba1 ...
Preparing to replace xorg-driver-fglrx 2:8.543-0ubuntu4 (using xorg-driver-fglrx_8.561-0ubuntu1_i386.deb) ...
Unpacking replacement xorg-driver-fglrx ...
Selecting previously deselected package xorg-driver-fglrx-dev.
Unpacking xorg-driver-fglrx-dev (from xorg-driver-fglrx-dev_8.561-0ubuntu1_i386.deb) ...
Setting up fglrx-kernel-source (2:8.561-0ubuntu1) ...
Adding Module to DKMS build system
rpmdb: lock_downgrade: Lock is no longer valid
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - Invalid argument (22)
error: cannot open Packages database in /var/lib/rpm
rpmdb: lock_downgrade: Lock is no longer valid
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - Invalid argument (22)
error: cannot open Packages database in /var/lib/rpm
rpmdb: lock_downgrade: Lock is no longer valid
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - Invalid argument (22)
error: cannot open Packages database in /var/lib/rpm
Doing initial module build
rpmdb: lock_downgrade: Lock is no longer valid
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - Invalid argument (22)
error: cannot open Packages database in /var/lib/rpm
rpmdb: lock_downgrade: Lock is no longer valid
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - Invalid argument (22)
error: cannot open Packages database in /var/lib/rpm
rpmdb: lock_downgrade: Lock is no longer valid
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - Invalid argument (22)
error: cannot open Packages database in /var/lib/rpm
Installing initial module
rpmdb: lock_downgrade: Lock is no longer valid
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - Invalid argument (22)
error: cannot open Packages database in /var/lib/rpm
rpmdb: lock_downgrade: Lock is no longer valid
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - Invalid argument (22)
error: cannot open Packages database in /var/lib/rpm
rpmdb: lock_downgrade: Lock is no longer valid
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - Invalid argument (22)
error: cannot open Packages database in /var/lib/rpm
Done.

Setting up fglrx-modaliases (2:8.561-0ubuntu1) ...
Setting up libamdxvba1 (2:8.561-0ubuntu1) ...

Setting up xorg-driver-fglrx (2:8.561-0ubuntu1) ...
Installing new version of config file /etc/ati/control ...
Installing new version of config file /etc/ati/amdpcsdb.default ...
Installing new version of config file /etc/ati/atiogl.xml ...
Installing new version of config file /etc/ati/signature ...

Processing triggers for man-db ...
Setting up xorg-driver-fglrx-dev (2:8.561-0ubuntu1) ...
Setting up fglrx-amdcccle (2:8.561-0ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
scott@scott-desktop:~/ati$ 

```

---

### Post by sdowney717 on 2008-12-20
I did not have to run ati-config --initial since I was just updating the version and here it is

---

