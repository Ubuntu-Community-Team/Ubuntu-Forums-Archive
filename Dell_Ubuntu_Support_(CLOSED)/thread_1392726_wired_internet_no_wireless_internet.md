---
title: "wired internet no wireless internet???"
date: 2010-01-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by schrummy on 2010-01-28
i have a dell inspiran 1500 series and i have internet when i use my ethernet cord but i have nothing when i try to go wireless.  i did clear my hard drive to put ubuntu onto my laptop (was vista and i was going crazy...) do not know it this might have been the cause to the issue or not.  
 
WARNING
 
im a noob to this operating system and have not yet figured out where anything is....

---

### Post by mikewhatever on 2010-01-28
If you have a Broadcom wireless card, search for **bcmwl-kernel-source** in Synaptic package manager, install the package and reboot. If that doesn't solve the problem, post the outputs of the following commands:

ifconfig

lshw -C network

---

### Post by schrummy on 2010-01-28
> **mikewhatever said:**
> If you have a Broadcom wireless card, search for **bcmwl-kernel-source** in Synaptic package manager, install the package and reboot. If that doesn't solve the problem, post the outputs of the following commands:

ifconfig

lshw -C network


ok searched for the kernel and i did not find anything.  Not completly sure if i have the wireless card or not.... as for the commands...
ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:1c:23:a7:63:d6  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:fea7:63d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4672 errors:1 dropped:1 overruns:0 frame:0
          TX packets:3922 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4845717 (4.8 MB)  TX bytes:604889 (604.8 KB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
 
```lshw -C network
```
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:fe8fc000-fe8fffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:a7:63:d6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 multicast=yes
       resources: irq:21 memory:fe5fe000-fe5fffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1e:4c:29:88:94
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
 
```

---

### Post by mikewhatever on 2010-01-28
Try the direct command:

sudo apt-get install bcmwl-kernel-source

Alternatively, check under System->Admin->Hardware Drivers. That last one is known to malfunction, but it wouldn't hurt trying.

---

### Post by schrummy on 2010-01-28
everything is working now... thank you very much kind sir...

---

