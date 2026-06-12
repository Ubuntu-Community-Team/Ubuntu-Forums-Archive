---
title: "Wireless failed following Hardy upgrade"
date: 2008-05-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by atatistcheff on 2008-05-09
I have an Inspiron 1420 which I installed the standard 7.10 distro on (not the Dell image).  This was working fine, then I upgraded to Hardy.  So far, I haven't seen any issues except that the wireless networking is hosed.  I'm using the internal card which I believe is a Broadcom.  It seems to possibly be a driver issue but I'm really not sure.  iwconfig shows eth1 has wireless extensions but that's as far as it goes.  Here's some ifconfig output:

**root@L33T:~# ifconfig eth1 up**
SIOCSIFFLAGS: No such file or directory

iwconfig:
**root@L33T:~# iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Here are some more commands and the output:

**root@L33T:~# ifup eth1**
ifup: interface eth1 already configured

**root@L33T:~# ifdown eth1**
There is already a pid file /var/run/dhclient.eth1.pid with pid 6430
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth1/00:1e:8c:2d:df:9a
Sending on   LPF/eth1/00:1e:8c:2d:df:9a
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 10.0.0.1 port 67
SIOCSIFFLAGS: No such file or directory

**root@L33T:~# ifup eth1**
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Could not set interface 'eth1' UP
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
wmaster0: unknown hardware address type 801
Listening on LPF/eth1/00:1e:8c:2d:df:9a
Sending on   LPF/eth1/00:1e:8c:2d:df:9a
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
send_packet: Network is down
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I'm not sure what else to try.

---

### Post by atatistcheff on 2008-05-09
Ok, replying to my own thread...

It was a rookie mistake.  Been too long since I upgraded.  Any "proprietary" drivers are automatically disabled so I had to go back to System->Administration->Hardware Drivers and enable the Broadcom card. Unfortunately, this requires a download from the Ubuntu archive and thus a network connection.  

Once again proving that you can't upgrade a laptop without a wired network connection. (well at least I can't)

Words of wisdom for anyone going down the same route.

---

### Post by Nico0020 on 2008-05-11
glad to hear you figured it out.  I lost my wireless on my Inspiron E1505 after upgrading, but only in my own home.  When I took it to my friends house, or on campus I could connect just fine.  But for some reason why trying to get hardy to connect to my 2wire dsl modem it just kills my modem to where nothing can connect until I reboot the modem and shut down the computer. :/

---

