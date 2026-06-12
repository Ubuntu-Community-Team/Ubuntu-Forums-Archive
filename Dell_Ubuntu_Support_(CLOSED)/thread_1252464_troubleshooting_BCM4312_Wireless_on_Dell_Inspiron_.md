---
title: "troubleshooting BCM4312 Wireless on Dell Inspiron 1545"
date: 2009-08-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rioguia on 2009-08-28
I had this working out of the box from Dell using the restricted driver provided by Dell with 8.04.  It worked again when I upgraded to 9.04.  It seems to have just stopped working.  

Here are my results for troubleshooting

sudo lshw

 *-network
                description: Wireless interface
                product: BCM4312 802.11b/g
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: eth1
                version: 01
                serial: 00:22:5f:af:28:da
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg

sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:off   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:23:ae:40:2b:b2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:22:5f:af:28:da  
          inet6 addr: fe80::222:5fff:feaf:28da/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1424 (1.4 KB)  TX bytes:1424 (1.4 KB)

pan0      Link encap:Ethernet  HWaddr 92:5d:74:f3:c3:e5  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lspci -v | grep subordinate
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
	Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	Bus: primary=00, secondary=0d, subordinate=0e, sec-latency=0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32

sudo ifconfig eth1 down
sudo ifconfig eth1 10.0.0.2 netmask 255.255.255.0
sudo route add default gw 10.0.0.1
sudo iwconfig eth1 essid "network_name"                              
sudo iwconfig eth1 mode managed key xxxxxxxxxxxxxxxxxxxxxxxxxx
sudo ifconfig eth1 up
ping 10.0.0.9 -c3

ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:23:ae:40:2b:b2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:22:5f:af:28:da  
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::222:5fff:feaf:28da/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2040 (2.0 KB)  TX bytes:2040 (2.0 KB)

pan0      Link encap:Ethernet  HWaddr 92:5d:74:f3:c3:e5  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:off   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


PING 10.0.0.9 (10.0.0.9) 56(84) bytes of data.
From 10.0.0.2 icmp_seq=1 Destination Host Unreachable
From 10.0.0.2 icmp_seq=2 Destination Host Unreachable
From 10.0.0.2 icmp_seq=3 Destination Host Unreachable

---

### Post by mikewhatever on 2009-08-30
It looks like the card is recognized and the module is loaded, also eth1 has the IP, 10.0.0.2. I don't see what's wrong.

---

### Post by rioguia on 2009-08-31
I think that this must be a freak hardware failure.  I finally gave up and bought an edimax mimo XR USB wireless nic.  I plugged in the nic and booted the machine.  The machine detected the nic automatically and connected to my secure wireless connection without configuration.

JUST AN UPDATE:  One of the kids stepped on the edimax.  It kept working for quite a while but it eventually deteriorated.  I replaced it with the Netgear WG111 v. 3 (WG 111, v.3).  Ubuntu 9.10 immediately detected the new hardware and loaded the new driver (rtl8187) without any configuration.

---

### Post by rioguia on 2010-07-28
The STA Wireless Driver solved this problem.  I noticed this new driver showed up when I randomly check the hardware driver manager since I first posted.  These package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4321-, andBCM4322-based hardware.

No need for external wireless!

---

