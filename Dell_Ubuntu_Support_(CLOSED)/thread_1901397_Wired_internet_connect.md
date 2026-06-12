---
title: "Wired internet connect"
date: 2011-12-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hebintn on 2011-12-28
I have a Dell Inspiron 1150 that I'm trying to set up with Ubuntu.  I tried 11.04 and could not get internet access.  So, I installed 11.10.  I still cannot get a wired connection going.  If I go to System settings/network/wired it tells me that the cable is unplugged and shows a hardware address for the computer.  The Network icon at the top shows a check by Enable Networking, and Wired Networks disconnected greyed out.  All boxes are checked automatic on the wired connection.  I plugged and unplugged the cable at both ends several times.  I checked continuity on the cable and it all pins are good.  I get an occasional light flicker on the router for the ethernet port I'm hooked to when I first boot.  The router and DSL is operational on my other devices.. desktop computer, and my wife's wireless connection and wireless printer works fine.  I tried manual setup on 11.04 without success... too many numbers that I don't know and my ISP said "We don't support this OS". (They should at least give me the numbers I need... pfft!  Jerks.)

I have the lspci and other outputs as requested listed below. Need anything else?  Correct me if I'm wrong, but it looks like there is no wireless hardware... right?

Thanks for you help.

Harry





harry@harry-Inspiron-1150:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02) 
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02) 
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02) 
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) 
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01) 
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01) 
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01) 
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81) 
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01) 
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01) 
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01) 
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01) 
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01) 
02:04.0 CardBus bridge: Texas Instruments PC


harry@harry-Inspiron-1150:~$ lsusb 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
harry@harry-Inspiron-1150:~$ 


harry@harry-Inspiron-1150:~$ lshw -class network 
WARNING: you should run this program as super-user. 
  *-network               
       description: Ethernet interface 
       product: BCM4401 100Base-T 
       vendor: Broadcom Corporation 
       physical id: 1 
       bus info: pci@0000:02:01.0 
       logical name: eth0 
       version: 01 
       serial: 00:0f:1f:22:46:eb 
       size: 10Mbit/s 
       capacity: 100Mbit/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=32 multicast=yes port=twisted pair speed=10Mbit/s 
       resources: irq:7 memory:fcffe000-fcffffff memory:fd000000-fd003fff 
WARNING: output may be incomplete or inaccurate, you should run this program as super-user. 
harry@harry-Inspiron-1150:~$ super-user. 
harry@harry-Inspiron-1150:~$ lshw -class network 
WARNING: you should run this program as super-user. 
  *-network               
       description: Ethernet interface 
       product: BCM4401 100Base-T 
       vendor: Broadcom Corporation 
       physical id: 1 
       bus info: pci@0000:02:01.0 
       logical name: eth0 
       version: 01 
       serial: 00:0f:1f:22:46:eb 
       size: 10Mbit/s 
       capacity: 100Mbit/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=32 multicast=yes port=twisted pair speed=10Mbit/s 
       resources: irq:7 memory:fcffe000-fcffffff memory:fd000000-fd003fff 
WARNING: output may be incomplete or inaccurate, you should run this program as super-user. 
harry@harry-Inspiron-1150:~$ 

harry@harry-Inspiron-1150:~$ uname -a 
Linux harry-Inspiron-1150 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux 
harry@harry-Inspiron-1150:~$ 

harry@harry-Inspiron-1150:~$ lsb_release -a 
No LSB modules are available. 
Distributor ID:	Ubuntu 
Description:	Ubuntu 11.10 
Release:	11.10 
Codename:	oneiric 
harry@harry-Inspiron-1150:~$ 


harry@harry-Inspiron-1150:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:0f:1f:22:46:eb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:138 errors:11 dropped:7 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:12119 (12.1 KB)  TX bytes:0 (0.0 B) 
          Interrupt:7 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:208 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:208 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:16416 (16.4 KB)  TX bytes:16416 (16.4 KB) 

harry@harry-Inspiron-1150:~$ 

harry@harry-Inspiron-1150:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

harry@harry-Inspiron-1150:~$ 


  harry@harry-Inspiron-1150:~$ route -n 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
harry@harry-Inspiron-1150:~$ 


harry@harry-Inspiron-1150:~$ ping -c 3 208.67.219.101 
connect: Network is unreachable 
harry@harry-Inspiron-1150:~$ 

harry@harry-Inspiron-1150:~$ ping -c 3 [www.opendns.com](www.opendns.com) 
ping: unknown host [www.opendns.com](www.opendns.com) 
harry@harry-Inspiron-1150:~$

---

### Post by 2F4U on 2011-12-28
Is there anything blacklisted, as in this post

[http://ubuntuforums.org/showthread.php?t=1631142](http://ubuntuforums.org/showthread.php?t=1631142)

There is another post that may be helpful:

[http://ubuntuforums.org/showthread.php?t=850342](http://ubuntuforums.org/showthread.php?t=850342)

---

