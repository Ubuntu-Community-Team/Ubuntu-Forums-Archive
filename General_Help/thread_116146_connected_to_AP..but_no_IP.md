---
title: "connected to AP..but no IP"
date: 2006-01-12
forum: General Help
---

### Post by closeyourwindows on 2006-01-12
I am using gateway solo 9300, with breezy 5.10 and for my network I have wpc54g Linksys card.  I installed gtkwifi and can see the wireless AP and can even connect to it using WEP.  The only thing I cannot do is obtain an IP address.  I am still stuck at loopback and unable to go forward on this.  I installed the drivers for the card and upon opening the network manager, I can see that the wireless card is activated with a wep code and it too says it is connected to the network.  what I cannot do is get out to the internet.  I checked the settings on the AP and it is set for dhcp.  I am sure the settings are correct on the router, just know that I am missing something minor.  :confused:

---

### Post by daschl on 2006-01-12
please post your iwconfig output :)

```

$ sudo iwconfig

```

if you know that its working, maybe you only have to do a

```

$ sudo dhclient eth1

```

(i suppose eth1 is your wireless network interface)

hth

---

### Post by ned.b on 2006-01-12
A few other things to consider...

Is MAC address filtering enabled on the router?  
If you are dual booting with another OS such as XP is that working ok?
If you don't use WEP does it work?

---

### Post by closeyourwindows on 2006-01-12
[QUOTE=ned.b]A few other things to consider...

Is MAC address filtering enabled on the router?  
If you are dual booting with another OS such as XP is that working ok?
If you don't use WEP does it work?[/QUOTE]

so MAC filtering is not on, and on the router settings I can see that there are 2 mac addresses on the router, one being the XP desktop and the other being the wireless.  I tested the card on another laptop with the same card and it was able to connect via dhcp..  and finally oddly enough when WEP was off it would not connect.

---

### Post by closeyourwindows on 2006-01-12
here are the errors I get while connecting

nate@solo:~$ sudo ifup wlan0
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0c:41:a9:f2:fa
Sending on   LPF/wlan0/00:0c:41:a9:f2:fa
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
nate@solo:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:DA:2F:16:9B
          inet addr:192.168.254.17  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::250:daff:fe2f:169b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:81 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:50380 (49.1 KiB)  TX bytes:13528 (13.2 KiB)
          Interrupt:9 Base address:0x4800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4749 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4749 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:431937 (421.8 KiB)  TX bytes:431937 (421.8 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0C:41:A9:F2:FA
          inet6 addr: fe80::20c:41ff:fea9:f2fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Memory:e800000-e801fff
nate@solo:~$ sudo iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

nate@solo:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:50:da:2f:16:9b
Sending on   LPF/eth0/00:50:da:2f:16:9b
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPNAK from 192.168.254.254
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.254.254
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.254.254
bound to 192.168.254.17 -- renewal in 1010404529 seconds.

nate@solo:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 7969
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0c:41:a9:f2:fa
Sending on   LPF/wlan0/00:0c:41:a9:f2:fa
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


I get all this while gtkwifi shows that I am connected at 100% and can find the SID and connect to it.  hmmmm.

---

### Post by closeyourwindows on 2006-01-13
I have reset the router and I know that did not have anything to do with it since I can connect to it from eth0 and other computer can connect to it with same card on xp (sorry).  wondering if I should remove all drivers and start all over again.  I downloaded wifi-radar and it too sees the access point. I took the laptop to work and it could see other access points as well but still the same problem, It is not getting assigned an IP address.  I suppose it is not a huge deal since I dont even have a battery for the laptop, and everything else works flawlessly, but any input would be appreciated.  
using 5.10 breezy, card is wpc54g-2, and the driver I am using is from linksys.

---

