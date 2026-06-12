---
title: "Compiling issue, wireless"
date: 2006-08-23
forum: Desktop Environments
---

### Post by tht00 on 2006-08-23
Alright -- I'm not unfamiliar with the compiling process of Linux or anything.  I've used Linux off-and-on for about a year, though, I'm not exactly sure where to go with this.  It's a program to help me get setup with Purdue's wireless connection.  Here's what happens when I run the install:
```
tom@tom-laptop:~$ cd Desktop/vpnclient/
tom@tom-laptop:~/Desktop/vpnclient$ ls
cisco_cert_mgr   IPSecDrvOSFunctions.h  linuxcniapi.h     vpnapi.h
Cniapi.h         IPSecDrvOS_linux.c     linuxkernelapi.c  vpnclient
config.h         IPSecDrvOS_linux.h     linux_os.h        vpnclient.ini
cvpnd            ipseclog               Makefile          vpnclient_init
driver_build.sh  libdriver.so           mtu.h             vpn_install
frag.c           libvpnapi.so           Purdue.pcf        vpn_ioctl_linux.h
frag.h           license.rtf            sample.pcf        vpn_uninstall
GenDefs.h        license.txt            unixcniapi.h
interceptor.c    linuxcniapi.c          unixkernelapi.h
tom@tom-laptop:~/Desktop/vpnclient$ sudo ./vpn_install
Cisco Systems VPN Client Version 4.7.00 (0640) Linux Installer
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms.


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.15-26-686/build]
* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.15-26-686/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.15-26-686/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.15-26-686/build SUBDIRS=/home/tom/Desktop/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-686'
  CC [M]  /home/tom/Desktop/vpnclient/linuxcniapi.o
/home/tom/Desktop/vpnclient/linuxcniapi.c: In function ‘CniInjectReceive’:
/home/tom/Desktop/vpnclient/linuxcniapi.c:292: error: ‘struct sk_buff’ has no member named ‘stamp’
/home/tom/Desktop/vpnclient/linuxcniapi.c: In function ‘CniInjectSend’:
/home/tom/Desktop/vpnclient/linuxcniapi.c:432: error: ‘struct sk_buff’ has no member named ‘stamp’
make[2]: *** [/home/tom/Desktop/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/tom/Desktop/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-686'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
tom@tom-laptop:~/Desktop/vpnclient$

```

I'm pretty sure it has to do with my kernel source.  I'm not even sure that I've got it installed, and if so, where it put it.  Thoughts?  BTW, the tarball is attached, and here's the instructions: [http://www.itap.purdue.edu/airlink/client/linux.cfm](http://www.itap.purdue.edu/airlink/client/linux.cfm)

At this point, I just want to be able to connect to the network... I've tried another method, using 'NetworkManager Applet' that *should've* worked (it uses WPA Enterprise).  In any case, my network situation is a little messy right now. :-k 

Thanks.

---

