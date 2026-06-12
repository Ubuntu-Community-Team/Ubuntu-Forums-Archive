---
title: "Dell Mini wireless help"
date: 2011-01-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jhra on 2011-01-11
I have a Dell Mini 1018 that I am unable to get proper drivers running on for the wireless. Can anyone point me to possible fixes here?


As per the "Can't connect to the internet" FAQ, I have the following information for any assistance with this. 


:~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
07:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)


:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:074f Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 004: ID 174f:1127 Syntek 
Bus 001 Device 002: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


:~$ lshw -class network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 05
       serial: 5c:26:0a:1e:4b:a4
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.65 latency=0 multicast=yes
       resources: irq:42 ioport:2000(size=256) memory:f0f2c000-f0f2cfff memory:f0f18000-f0f1bfff
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:f0100000-f0103fff



[B]Internet service provider is Telus

I am using Ubuntu 10.10 and was trying this with Ubuntu Remix as well

I am currently online via. hard line.[/B]

:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 5c:26:0a:1e:4b:a4  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::5e26:aff:fe1e:4ba4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4782 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4162 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5273149 (5.2 MB)  TX bytes:622498 (622.4 KB)
          Interrupt:42 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)


:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0



:~$ ping -c 3 208.67.219.101
PING 208.67.219.101 (208.67.219.101) 56(84) bytes of data.

--- 208.67.219.101 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1998ms


:~$ ping -c 3 [www.opendns.com](www.opendns.com)
PING [www.opendns.com](www.opendns.com) (208.69.38.150) 56(84) bytes of data.
64 bytes from 208.69.38.150: icmp_req=1 ttl=52 time=82.6 ms
64 bytes from 208.69.38.150: icmp_req=2 ttl=52 time=73.3 ms
64 bytes from 208.69.38.150: icmp_req=3 ttl=52 time=73.0 ms

--- [www.opendns.com](www.opendns.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 10326ms
rtt min/avg/max/mdev = 73.025/76.317/82.612/4.452 ms



**I am not dual booting this system. **


Thus far I have attempted to use the step by step fixes from [ubuntumini.com]("http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html") with no fix.

---

### Post by mikewhatever on 2011-01-12
The ubuntumini.com solution would have worked, had you had a Broadcom wireless card. According to the outputs, you have a Realtec, which requires a different driver. Here is a recent thread with the same problem:
[http://ubuntuforums.org/showthread.php?t=1658112&page=2](http://ubuntuforums.org/showthread.php?t=1658112&page=2)

Before trying the suggested solution, remove the broadcom module:
```
sudo apt-get purge bcmwl-kernel-source
```

---

### Post by jhra on 2011-01-12
Thanks, by running "sudo lshw -class network" I just found this. Now back to square one, I will post my progress as I can.




:~$ sudo lshw -class network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 05
       serial: 5c:26:0a:1e:4b:a4
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.65 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:26 ioport:2000(size=256) memory:f0f2c000-f0f2cfff(prefetchable) memory:f0f18000-f0f1bfff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:f0100000-f0103fff

---

### Post by jhra on 2011-01-14
Fixed... would have helped if I just looked in the Ubuntu Software Centre. 


On the bright side, I learned a ton.

---

