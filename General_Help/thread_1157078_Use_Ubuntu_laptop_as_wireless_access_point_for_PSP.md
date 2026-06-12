---
title: "Use Ubuntu laptop as wireless access point for PSP?"
date: 2009-05-12
forum: General Help
---

### Post by crazyfuturamanoob on 2009-05-12
PSP says "no access points found". (with windows psp finds access point and can connect internet)

This laptop is Acer Aspire 7520g so you can google the wifi card and hardware info.

```

**$ iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

pan0      no wireless extensions.


```

```

**$ ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:1b:38:e1:9a:70  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:251 

eth1      Link encap:Ethernet  HWaddr 00:11:e3:9d:89:98  
          inet addr:91.156.170.127  Bcast:91.156.175.255  Mask:255.255.240.0
          inet6 addr: fe80::211:e3ff:fe9d:8998/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2403 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1669 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1778722 (1.7 MB)  TX bytes:296712 (296.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8996 (8.9 KB)  TX bytes:8996 (8.9 KB)


```

```

**$ sudo lshw -C network**
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:38:e1:9a:70
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
  *-network:0
       description: Ethernet interface
       physical id: 1
       logical name: eth1
       serial: 00:11:e3:9d:89:98
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=CDC Ethernet Device ip=91.156.170.127 link=yes multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 26:5c:8c:20:1d:3c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

I enabled madwifi from System->Administration->Hardware drivers. No effect.

---

### Post by crazyfuturamanoob on 2009-05-13
Am I not clear enough?

---

