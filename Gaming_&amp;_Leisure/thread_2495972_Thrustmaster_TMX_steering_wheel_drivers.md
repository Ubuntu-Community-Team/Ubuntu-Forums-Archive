---
title: "Thrustmaster TMX steering wheel drivers"
date: 2024-03-10
forum: Gaming &amp; Leisure
---

### Post by wildbillkelso1941 on 2024-03-10
Hi. I am trying to get my Thrustmaster TMX steering wheel working to use it for driving games on Steam. I am using Xubuntu 23.10 minimal. I have installed build-essential and DKMS and trying to use this driver.
[https://github.com/scarburato/t150_driver](https://github.com/scarburato/t150_driver)
running sudo ./install.sh again I get the following.

==== REMOVING OLD VERSIONS ====
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/t150/0.8a/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/t150/0.8a/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/t150/0.8a/source/dkms.conf)
Module t150-0.8a for kernel 6.5.0-21-generic (x86_64).
Before uninstall, this module version was ACTIVE on this kernel.

hid-t150.ko.zst:
 - Uninstallation
   - Deleting from: /lib/modules/6.5.0-21-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.
depmod...
Deleting module t150-0.8a completely from the DKMS tree.
rmmod: ERROR: Module hid_t150 is not currently loaded
==== CONFIG DKMS ====
mkdir: cannot create directory ‘/usr/src/t150-0.8a’: File exists
mkdir: cannot create directory ‘/usr/src/t150-0.8a/build’: File exists
==== DKMS ====
Deprecated feature: REMAKE_INITRD (/usr/src/t150-0.8a/dkms.conf)
Creating symlink /var/lib/dkms/t150/0.8a/source -> /usr/src/t150-0.8a
Sign command: /usr/bin/kmodsign
Signing key: /var/lib/shim-signed/mok/MOK.priv
Public certificate (MOK): /var/lib/shim-signed/mok/MOK.der
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/t150/0.8a/source/dkms.conf)

Building module:
make KDIR=/lib/modules/6.5.0-21-generic/build clean
make -C ./hid-t150 clean
make[1]: Entering directory '/var/lib/dkms/t150/0.8a/build/hid-t150'
make -C /lib/modules/6.5.0-21-generic/build M=/var/lib/dkms/t150/0.8a/build/hid-t150 clean
make[2]: Entering directory '/usr/src/linux-headers-6.5.0-21-generic'
make[2]: Leaving directory '/usr/src/linux-headers-6.5.0-21-generic'
make[1]: Leaving directory '/var/lib/dkms/t150/0.8a/build/hid-t150'
rm -rf ./build/*

{ make -j12 KERNELRELEASE=6.5.0-21-generic KDIR=/lib/modules/6.5.0-21-generic/build all; } >> /var/lib/dkms/t150/0.8a/build/make.log 2>&1

Signing module /var/lib/dkms/t150/0.8a/build/build/hid-t150.ko
make KDIR=/lib/modules/6.5.0-21-generic/build clean
make -C ./hid-t150 clean
make[1]: Entering directory '/var/lib/dkms/t150/0.8a/build/hid-t150'
make -C /lib/modules/6.5.0-21-generic/build M=/var/lib/dkms/t150/0.8a/build/hid-t150 clean
make[2]: Entering directory '/usr/src/linux-headers-6.5.0-21-generic'
  CLEAN   /var/lib/dkms/t150/0.8a/build/hid-t150/Module.symvers
make[2]: Leaving directory '/usr/src/linux-headers-6.5.0-21-generic'
make[1]: Leaving directory '/var/lib/dkms/t150/0.8a/build/hid-t150'
rm -rf ./build/*

Deprecated feature: REMAKE_INITRD (/var/lib/dkms/t150/0.8a/source/dkms.conf)

hid-t150.ko.zst:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/6.5.0-21-generic/updates/dkms/
do_depmod 6.5.0-21-generic

==== INSTALLING UDEV RULES ====
'./files/etc/udev/rules.d/10-t150.rules' -> '/etc/udev/rules.d/10-t150.rules'
==== LOADING NEW MODULES ====


The UDEV rule had been copied to the UDEV folder and running lsusb the device appears as 
Bus 001 Device 004: ID 044f:b67e ThrustMaster, Inc. Thrustmaster TMX GIP Racing Wheel
The wheel is not working on the Xubuntu PC but it is working on the Xbox so I am obviously missing something or doing something stupid and more steps are needed to get it to work.

Any advice or assistance to get this working would be very much appreciated.

Kind regards.

---

### Post by keshara283 on 2024-05-11
Hi, did you end up finding a solution to this?

I also have a Thrustmaster TMX Pro sitting in my closet, but I've been under the assumption for a while now that the TMX just isn't compatible with Linux at all. However, last time I researched this was probably 2 years ago now. 

Would love to have the ability to get back into some sim racing on my Linux machine

---

