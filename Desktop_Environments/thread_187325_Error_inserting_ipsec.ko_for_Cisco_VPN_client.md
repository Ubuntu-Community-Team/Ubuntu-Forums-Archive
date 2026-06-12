---
title: "Error inserting ipsec.ko for Cisco VPN client"
date: 2006-06-02
forum: Desktop Environments
---

### Post by LittleLebowski on 2006-06-02
I have the correct headers installed.  I am at my wit's end here.  Does anybody know what I'm missing to get the Cisco VPN client running?  Accepted the defaults and it installs but does not work.


Starting /opt/cisco-vpnclient/bin/vpnclient: insmod: error inserting '/lib/modules/2.6.15-23-686/CiscoVPN/cisco_ipsec.ko': -1 Invalid module format
Failed (insmod)

---

### Post by LittleLebowski on 2006-06-02
I checked uname -r, ensured that I have the correct kernel headers installed, and I also have GCC 3.4 installed.  What am I missing?

---

### Post by LittleLebowski on 2006-06-03
After an hour of playing around, I can't even compile the darned thing.  KVPNC crashes with no explanation.  I'm trying to connect to my own PIX at work.

  Can somebody post what packages I need on an 686 kernel to get this working?  Do I need to select GCC 3.4 somehow or just have it installed?  Do I need symbolic links in /usr/src/?

---

### Post by LittleLebowski on 2006-06-03
Here's what happens.  

sh vpn_install
Cisco Systems VPN Client Version 4.7.00 (0640) Linux Installer
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms.


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.15-23-686/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.15-23-686/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.15-23-686/build" will be used to build the module.

Is the above correct [y]

Shutting down /opt/cisco-vpnclient/bin/vpnclient: module cisco_ipsec is not running.
Stopped: /etc/init.d/vpnclient_init (VPN init script)
Making module
make -C /lib/modules/2.6.15-23-686/build SUBDIRS=/home/bax/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-23-686'
  CC [M]  /home/bax/vpnclient/linuxcniapi.o
/home/bax/vpnclient/linuxcniapi.c: In function ‘CniInjectReceive’:
/home/bax/vpnclient/linuxcniapi.c:292: error: ‘struct sk_buff’ has no member named ‘stamp’
/home/bax/vpnclient/linuxcniapi.c: In function ‘CniInjectSend’:
/home/bax/vpnclient/linuxcniapi.c:432: error: ‘struct sk_buff’ has no member named ‘stamp’
make[2]: *** [/home/bax/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/bax/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-23-686'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
root@ubuntu:/home/bax/vpnclient#

---

### Post by LittleLebowski on 2006-06-03
Using the 4.8 version of the client magically fixed all of my problems.

---

### Post by dmflad on 2006-06-04
I too was loosing hair over Cisco VPN until I used 4.8 version of client AND aptitude command to get the correct headers. ](*,) Once I had correct headers the install went okay. I can now VPN into work - but can only do it by running Cisco VPN Client from command line. KVpnc crashes when ever I try to import Cisco .pcf file so I gave up on that.  Next battle is BroadComm Wireless card in this Dell D600...

---

### Post by williamx on 2006-06-11
Where did you get the 4.8 version of the vpn-client? My school doesn't provide me with any newer than 4.6...

---

### Post by cajunlibra on 2007-10-18
deleted by user

---

### Post by cajunlibra on 2007-10-18
Found the solution [here:]("http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/")

Be sure to scroll down to the bottom of the page for the new version of the Cisco VPN client.

---

