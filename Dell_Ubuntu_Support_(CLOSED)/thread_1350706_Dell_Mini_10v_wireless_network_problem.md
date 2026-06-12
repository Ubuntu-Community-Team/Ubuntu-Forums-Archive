---
title: "Dell Mini 10v wireless network problem"
date: 2009-12-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by liekomg on 2009-12-09
I just received my Dell Mini10v with Windows XP SP3 installed. It's able to detect wireless networks. However, I installed Ubuntu Netbook Remix 9.10 by Wubi; everything works fine except the network settings. I does not find the network for my house I am using. Does anyone else have issues with finding wireless networks on the Dell Mini10v using Ubuntu?

Here are my details based on [[COLOR=#d40000]**ugm6hr**[/COLOR]]("http://ubuntuforums.org/member.php?u=103883")'s lists of questions:

I am using Cox Digital Cable in Virginia
I am online with my other laptop using windows 7


               mike@ubuntu:~$ lspci  
 00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)  
 00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)  
 00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)  
 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)  
 00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)  
 00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)  
 00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)  
 00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)  
 00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)  
 00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)  
 00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)  
 00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)  
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)  
 00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)  
 00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)  
 00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)  
 03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)  
 04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)  
 mike@ubuntu:~$ lsusb  
 Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device  
 Bus 001 Device 002: ID 174f:1403 Syntek 
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 mike@ubuntu:~$ lshw -class network  
 WARNING: you should run this program as super-user.  
   *-network                
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
        resources: irq:17 memory:f0100000-f0103fff  
   *-network  
        description: Ethernet interface  
        product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller  
        vendor: Realtek Semiconductor Co., Ltd.  
        physical id: 0  
        bus info: pci@0000:04:00.0  
        logical name: eth0  
        version: 02  
        serial: 00:24:e8:e7:fe:78  
        width: 64 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list rom ethernet physical  
        configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes  
        resources: irq:27 ioport:2000(size=256) memory:f0510000-f0510fff(prefetchable) memory:f0500000-f050ffff(prefetchable) memory:f0520000-f053ffff(prefetchable)  
 mike@ubuntu:~$ uname -a  
 Linux ubuntu 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux  
 mike@ubuntu:~$ lsb_release -a  
 No LSB modules are available.  
 Distributor ID:    Ubuntu  
 Description:    Ubuntu 9.10  
 Release:    9.10  
 Codename:    karmic  
 mike@ubuntu:~$ ifconfig  
 eth0      Link encap:Ethernet  HWaddr 00:24:e8:e7:fe:78   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:27 Base address:0x6000  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:4 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:4 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)  
 

 mike@ubuntu:~$ iwconfig  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 mike@ubuntu:~$ route -n  
 Kernel IP routing table  
 Destination     Gateway         Genmask         Flags Metric Ref    Use Iface  
 mike@ubuntu:~$ ping -c 3 208.67.219.101 
 connect: Network is unreachable  
 mike@ubuntu:~$ ping -c 3 [www.opendns.com]("http://www.opendns.com")  
 ping: unknown host [www.opendns.com]("http://www.opendns.com")  
 mike@ubuntu:~$ ^C  
 mike@ubuntu:~$

---

### Post by ugm6hr on 2009-12-09
I am still on 9.04, and have a Mini 9, and didn't use Wubi, so I can't help much.

But have you read this: [http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

---

### Post by liekomg on 2009-12-09
SOLVED! ty ty ty ty :)

---

