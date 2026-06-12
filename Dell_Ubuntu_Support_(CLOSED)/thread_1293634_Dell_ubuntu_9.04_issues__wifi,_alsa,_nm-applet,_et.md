---
title: "Dell ubuntu 9.04 issues : wifi, alsa, nm-applet, etc.. help help"
date: 2009-10-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kuttan on 2009-10-17
I have Dell inspiron 6400, recently upgraded to 9.04. There are some issues, some of them carry fwded from 8.10.

**Issue 1.** While booting, every time it stops for a while at "building kernel modules for 2.6.28-15...." (may not be exactly same wordings, but some thing like that). And says "Build failed, see /var/run/alsa-driver.2628.log"
 
Last a few lines /var/run/alsa-driver.2628.log says:

/usr/lib/alsa-driver-linuxant/include/adriver.h:744: error: previous declaration of 'snd_compat_vmalloc_to_page' was here
In file included from /usr/lib/alsa-driver-linuxant/acore/hwdep.c:1:
/usr/lib/alsa-driver-linuxant/include/adriver.h: In function 'snd_pci_orig_save_state':
/usr/lib/alsa-driver-linuxant/include/adriver.h:1182: error: too many arguments to function 'pci_save_state'
/usr/lib/alsa-driver-linuxant/include/adriver.h: In function 'snd_pci_orig_restore_state':
/usr/lib/alsa-driver-linuxant/include/adriver.h:1186: error: too many arguments to function 'pci_restore_state'
make[3]: *** [/usr/lib/alsa-driver-linuxant/acore/hwdep.o] Error 1
make[2]: *** [/usr/lib/alsa-driver-linuxant/acore] Error 2
make[1]: *** [_module_/usr/lib/alsa-driver-linuxant] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [compile] Error 2

**Issue 2** nm-applet on the top of the screen has 'x' red sign on it. It has grey writings :"Wired network //device not managed//Wireless networks//device not managed." Only "vpn connections" is 'clickable'.

**Issue 3** Each time I have to do sudo ifup eth0 to get lan working. Why is it not done while booting? May be related to **2**

**Issue 4** Wifi not working.  From network-config, scan wifi networks show all available networks in the area.
when test it, getting following error:

Configuring device eth1 :

$ iwconfig eth1 mode managed

$ iwconfig eth1 essid "swaswe"

$ iwconfig eth1 rate auto

$ iwconfig eth1 key off

$ pkill wpa_supplicant

$ wpa_supplicant -B -Dndiswrapper -ieth1 -c/etc/wpa_supplicant/wpa_psk.conf
Unsupported driver 'ndiswrapper'.

$ ifconfig eth1 up

DHCP may take a while, please wait...
$ dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 9854
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth1/00:18:de:a5:7a:e2
Sending on   LPF/eth1/00:18:de:a5:7a:e2
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I had issues 2,3 and 4 on 8.10, thought will be fixed once I upgrade (except wifi as it seems related to driver)

Please help

---

### Post by kuttan on 2009-10-18
**Solved one !!**
If any of you are facing these issues: This thread solved my wifi issue. Now it connects to my wireless router!!
[http://ubuntuforums.org/showpost.php?p=6855351&postcount=15](http://ubuntuforums.org/showpost.php?p=6855351&postcount=15)

I also commented out auto eth1.

:P:P:P

---

### Post by kuttan on 2009-10-26
Solved alsa-driver issue by following this thread.

[http://ubuntuforums.org/showthread.php?p=7227161](http://ubuntuforums.org/showthread.php?p=7227161)

:-)

---

