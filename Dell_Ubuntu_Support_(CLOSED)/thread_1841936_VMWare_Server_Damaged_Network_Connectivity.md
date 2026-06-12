---
title: "VMWare Server Damaged Network Connectivity"
date: 2011-09-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by RSASKA on 2011-09-10
Have a problem.

- I have Ubuntu 9.04 on Dell 1545

- Installed VMWare Server, accepted all default values

- Attempted to add virtual machine, Win XP guest operating system

- After several failed attempts for Win XP to load, kept pressing F2 while virtual machine was loading to that Win XP would install

- Suddenly, my wireless connectivity failed


Did a complete ERASE and re-install of Ubuntu 9.04

In the past when I did a complete ERASE and re-install, Ubuntu would detect nearby wireless connections, and I would authenticate and connect to my home wireless network.

Now, it does not detect any wireless networks at all.

My other laptop connects to the wireless network just fine, but I need the Ubuntu to be online.

Please tell me how to troubleshoot and resolve this.

---

### Post by RSASKA on 2011-09-10
I managed to get a WIRED connection, I copied and pasted the output of the following commands:

**$ sudo ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:25:64:5a:e2:f8  
          inet addr:192.168.1.42  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:64ff:fe5a:e2f8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:178 errors:0 dropped:0 overruns:0 frame:0
          TX packets:115 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:108120 (108.1 KB)  TX bytes:15039 (15.0 KB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 70:1a:04:24:e6:e7  
          inet6 addr: fe80::721a:4ff:fe24:e6e7/64 Scope:Link
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
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7420 (7.4 KB)  TX bytes:7420 (7.4 KB)



[B]$ sudo iwconfig
[/B]lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power: ff   
          Retry min limit:7   RTS thr: ff   Fragment thr:ff
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.



**$ sudo lshw -class Network**
    *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 70:1a:04:24:e6:e7
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:5a:e2:f8
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.1.42 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 82:24:c2:b8:c5:5e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by RSASKA on 2011-09-10
Attempted to follow the instructions on [http://ubuntuguides.blogspot.com/2008/11/setting-up-internet-connection.html](http://ubuntuguides.blogspot.com/2008/11/setting-up-internet-connection.html)

I downloaded and extracted ndiswrapper-1.57rc1.tar.gz to ndiswrapper-1.57rc1.

On the terminal I navigated to ndiswrapper-1.57rc1 and typed [FONT=Arial]make[/FONT].

I thought this would install the wireless driver, unfortunately, it did not.

I went to Applications > Add/Remove > In Search typed ndis.

When I attempted to install, I got error in attached screenshot (ndis_cannot_install.png)

How can I get wireless connection again?

When I go to System > Administration > Hardware Devices

it shows that Broadcom is enabled (attached screenshot broadcom.png)

I even followed directions on [http://ubuntuforums.org/showthread.php?t=1061710&page=2](http://ubuntuforums.org/showthread.php?t=1061710&page=2) and went to [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) and followed the directions, but still no luck.

I needed VMWare to do something for work, it seems that VMWare did something to wireless drivers, now I am at my wits end. I cannot even do the thing for work that I am supposed to do and am even more behind.

Please advise how to fix this at the earliest.

---

### Post by RSASKA on 2011-09-10
I believed the following solved my problem

- plugged in ethernet
- did clean install


Now I can access the Internet via wireless

---

