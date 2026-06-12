---
title: "wmaster0 and wlan0"
date: 2008-06-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by SheridanLake on 2008-06-09
Can't connect using wireless Intel 3945 on Dell latitude D820 Hardy 8.04.  Note intel shows as wmaster0 with lshw -C network but IFCONFIG shows wmaster0 and wlan0  Tried backports and Wicd but can't connect.  Help anyone.  Thx

 *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:37:ff:b8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 mult

IFCONFIG:
wlan0     Link encap:Ethernet  HWaddr 00:18:de:37:ff:b8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-37-FF-B8-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by broomie on 2009-02-21
what worked for me was adding the line iwl3945 to /etc/modules and re booting

this was mentioned elsewhere on these forums

Dell m1330 intel3945 intrepid

---

