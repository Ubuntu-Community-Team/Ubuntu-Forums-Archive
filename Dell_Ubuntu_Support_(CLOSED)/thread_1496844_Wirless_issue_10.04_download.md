---
title: "Wirless issue 10.04 download"
date: 2010-05-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by PinkFloydGuy on 2010-05-29
I just booted up my netbook with the new "ubuntu 10.04 netbook remix" and imediatly i noticed my wireless was not working.  I looked up the issue and found it was a common problem, downloaded the wireless driver and restarted my computer and hoped for the best.  Now, when i click on the wireless connection icon it can regonize my wireless internet but when i go to connect to it, it wont allow me to. It just pulses and never connects. PLEASE HELP!!!

---

### Post by ugm6hr on 2010-05-30
Please give details from questions in Wifi help link below.

---

### Post by PinkFloydGuy on 2010-05-30
Hey thanks for link I'll just number my list as you have it.

1. Trying to get online with a modem/router all in one thingy.  Its a seimens corp. gigaset something.

2.   *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:f6:4e:a1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.254.4 latency=0 multicast=yes
       resources: irq:27 ioport:2000(size=256) memory:f0610000-f0610fff(prefetchable) memory:f0600000-f060ffff(prefetchable) memory:f0620000-f063ffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:23:08:53:47:c7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

3.  Internet service provider is frontiernet NEW YORK

4.  ramone@ramone-laptop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04 LTS
Release:    10.04
Codename:    lucid

5.  i can get online useing an ethernet cord totaly fine. But i need my wireless to work. 

7.

eth0      Link encap:Ethernet  HWaddr 00:21:70:f6:4e:a1  
          inet addr:192.168.254.4  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::221:70ff:fef6:4ea1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5637 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5097 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7398806 (7.3 MB)  TX bytes:524039 (524.0 KB)
          Interrupt:27 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:164 errors:0 dropped:0 overruns:0 frame:0
          TX packets:164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12672 (12.6 KB)  TX bytes:12672 (12.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:23:08:53:47:c7  
          inet6 addr: fe80::223:8ff:fe53:47c7/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1296 (1.2 KB)

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.254.0   0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.254.254 0.0.0.0         UG    0      0        0 eth0


ramone@ramone-laptop:~$ ping -c 3 208.67.219.101
PING 208.67.219.101 (208.67.219.101) 56(84) bytes of data.

ramone@ramone-laptop:~$ ping -c 3 [www.opendns.com](www.opendns.com)
PING [www.opendns.com](www.opendns.com) (208.69.38.150) 56(84) bytes of data.
64 bytes from 208.69.38.150: icmp_seq=1 ttl=51 time=407 ms
64 bytes from 208.69.38.150: icmp_seq=2 ttl=51 time=363 ms
64 bytes from 208.69.38.150: icmp_seq=3 ttl=51 time=830 ms

--- [www.opendns.com](www.opendns.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 11171ms
rtt min/avg/max/mdev = 363.510/533.768/830.107/210.318 ms


8. not sure what this step means. Im a linux NEWBIE!!! It sucks.

---

### Post by ugm6hr on 2010-05-30
OK. You have the same wifi card as my Dell Mini 9.  Which means it should work with open, WEP, WPA encryptions at least.

However, you are using the b43 driver (see your lshw output), whereas I am using the wl0 driver.

My lshw:
```
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:23:08:19:c5:33
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f0200000-f0203fff

```

How did you install the driver?  I would suggest the following:
[http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html](http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html)

Hopefully, that will just replace your b43 driver.

---

### Post by PinkFloydGuy on 2010-05-30
Thank you for the info got it working perfectly!!!

---

