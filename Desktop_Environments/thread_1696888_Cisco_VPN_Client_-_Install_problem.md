---
title: "Cisco VPN Client - Install problem"
date: 2011-02-28
forum: Desktop Environments
---

### Post by inckiekage on 2011-02-28
I have a problem installing the Cisco VPN client on my 64bit Ubuntu.10.10

```
kimse@kimselaptop:~/Desktop/vpnclient$ sudo ./vpn_install 
Cisco Systems VPN Client Version 4.8.02 (0030) Linux Installer
Copyright (C) 1998-2006 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.35-25-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.35-25-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.35-25-generic/build" will be used to build the module.

Is the above correct [y]y

Making module
make -C /lib/modules/2.6.35-25-generic/build SUBDIRS=/home/kimse/Desktop/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-25-generic'
  CC [M]  /home/kimse/Desktop/vpnclient/linuxcniapi.o
/home/kimse/Desktop/vpnclient/linuxcniapi.c:14: fatal error: linux/autoconf.h: No such file or directory
compilation terminated.
make[2]: *** [/home/kimse/Desktop/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/kimse/Desktop/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
```

---

### Post by pn8830 on 2011-02-28
Hi,


I had the same problem. Here is what I did:

```
user@localhost:~/vpnclient$ find / -name autoconf.h -print 2>/dev/null
/usr/src/linux-headers-2.6.35-25-generic/include/generated/autoconf.h
/usr/src/linux-headers-2.6.35-22-generic/include/generated/autoconf.h


user@localhost:~/vpnclient$ grep linux/autoconf *
frag.c:#include <linux/autoconf.h>
interceptor.c:#include <linux/autoconf.h>
IPSecDrvOS_linux.c:#include <linux/autoconf.h>
linuxcniapi.c:#include <linux/autoconf.h>
user@localhost:~/vpnclient$
```

After that I edited every listed file and changed linux/autoconf.h to generated/autoconf.h (see the output of find command above). For some reason autoconf.h was in different directory. I'm not sure why.

Installation was successful after that.


Good Luck,
PN.

---

### Post by deconstrained on 2011-02-28
> **pn8830 said:**
> After that I edited every listed file and changed linux/autoconf.h to generated/autoconf.h (see the output of find command above).
Better yet, make a symbolic link, after double-checking that autoconf is installed in the first place

---

### Post by inckiekage on 2011-03-04
> **deconstrained said:**
> Better yet, make a symbolic link, after double-checking that autoconf is installed in the first place

I followed your advise creating a symbolic link

like this
```
kimse@kimselaptop:/usr/src/linux-headers-2.6.35-27-generic/include/linux$ sudo ln -s ../generated/autoconf.h autoconf.h
```

Compiling
```
Making module
make -C /lib/modules/2.6.35-27-generic/build SUBDIRS=/home/kimse/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-27-generic'
  CC [M]  /home/kimse/vpnclient/linuxcniapi.o
  CC [M]  /home/kimse/vpnclient/frag.o
  CC [M]  /home/kimse/vpnclient/IPSecDrvOS_linux.o
  CC [M]  /home/kimse/vpnclient/interceptor.o
/home/kimse/vpnclient/interceptor.c: In function &#8216;interceptor_init&#8217;:
/home/kimse/vpnclient/interceptor.c:132: error: &#8216;struct net_device&#8217; has no member named &#8216;hard_start_xmit&#8217;
/home/kimse/vpnclient/interceptor.c:133: error: &#8216;struct net_device&#8217; has no member named &#8216;get_stats&#8217;
/home/kimse/vpnclient/interceptor.c:134: error: &#8216;struct net_device&#8217; has no member named &#8216;do_ioctl&#8217;
/home/kimse/vpnclient/interceptor.c: In function &#8216;add_netdev&#8217;:
/home/kimse/vpnclient/interceptor.c:271: error: &#8216;struct net_device&#8217; has no member named &#8216;hard_start_xmit&#8217;
/home/kimse/vpnclient/interceptor.c:272: error: &#8216;struct net_device&#8217; has no member named &#8216;hard_start_xmit&#8217;
/home/kimse/vpnclient/interceptor.c: In function &#8216;remove_netdev&#8217;:
/home/kimse/vpnclient/interceptor.c:294: error: &#8216;struct net_device&#8217; has no member named &#8216;hard_start_xmit&#8217;
make[2]: *** [/home/kimse/vpnclient/interceptor.o] Error 1
make[1]: *** [_module_/home/kimse/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-27-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko"
```

---

### Post by deconstrained on 2011-03-04
Come to think of it I've run into this exact same problem before. It's because the kernel sources/libraries changed, and Cisco never bothered to update their client to reflect those changes, so it only compiles with earlier kernels.

As I recall, I gave up and used 'vpnc', which is a Cisco-compatible VPN client that is open-source (and available in the Ubuntu repos). If your company/organization gave you some PCF files, there's a script you'll need to run to convert them to the format that vpnc can read/understand;

[http://baheyeldin.com/cisco/converting-cisco-easy-vpn-pcf-files-linux-vpnc-configuration-format.html](http://baheyeldin.com/cisco/converting-cisco-easy-vpn-pcf-files-linux-vpnc-configuration-format.html)

---

### Post by sentinelace on 2011-08-04
> **deconstrained said:**
> Come to think of it I've run into this exact same problem before. It's because the kernel sources/libraries changed, and Cisco never bothered to update their client to reflect those changes, so it only compiles with earlier kernels.
 
As I recall, I gave up and used 'vpnc', which is a Cisco-compatible VPN client that is open-source (and available in the Ubuntu repos). If your company/organization gave you some PCF files, there's a script you'll need to run to convert them to the format that vpnc can read/understand;
 
[http://baheyeldin.com/cisco/converting-cisco-easy-vpn-pcf-files-linux-vpnc-configuration-format.html](http://baheyeldin.com/cisco/converting-cisco-easy-vpn-pcf-files-linux-vpnc-configuration-format.html)
 
This is kind of where I am but I cannot get vpnc to work either.  I entered all the IP information but then I get an error saying it cannot find the myconf file.

---

