---
title: "After upgrading from 10.04 to 12.04, lost all internet connectivity"
date: 2012-11-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by schrummy on 2012-11-06
i have a dell inspiron 1521, before upgrading to 12.04, my laptop ran fine.  connected via LAN and wifi.  after the upgrade my computer will not connect to the internet in anyway.  I know its normal for my wifi to not work after an upgrade or fresh install, however this is the first time that wiring the laptop directly to the router did not work.  

Typing ifconfig -a into terminal results in the following
```
Link encap:Local Loopback
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr:  ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:4436 errors:0 dropped:0 overruns:0 frame:0
TX packets:4436 errors:0 dropped:0 overruns:0 carriers:0
collisions:0 txqueuelen:0
RX bytes:353112 (353.1 KB)  TX bytes:353112 (353.1 KB)
```

typed that from my laptop so spacing on somethings may be wrong...  any help would be fantastic

---

### Post by schrummy on 2012-11-06
bump for new eyes

---

### Post by uclugLee on 2012-11-07
It appears, if that's all that is appearing in the terminal when running that command, that the WAN and LAN ports are no longer being recognized by the computer.  However, I've also never upgraded two versions before.  I upgraded from 11.04 to 12.04 with no issues though.

When you click in the network icon in the upper right corner, does it say if your wired and/or wireless network are disabled?

You may want to try picking up a USB wireless adapter and see if you can access the internet using that.  If you can you may want to search network updates.

---

### Post by ugm6hr on 2012-11-10
Read and respond to points 2 & 9 at:
[http://ubuntuforums.org/showpost.php?p=5024425&postcount=1](http://ubuntuforums.org/showpost.php?p=5024425&postcount=1)

And you can copy & paste onto a USB drive to upload rather than typing things out.

---

### Post by schrummy on 2012-11-10
I ended up reinstalling 12.04....  my ethernet port now works... however the wifi is not.... 
here are the answers to what you asked for ugm6hr
2.
```
:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RS690 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (PCI Express Port 1)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB600 Non-Raid-5 SATA
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI0)
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI1)
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI2)
00:13.3 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI3)
00:13.4 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI4)
00:13.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB Controller (EHCI)
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB600 IDE
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB600 PCI to LPC Bridge
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS690M [Radeon X1200 Series]
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01
```

```
:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RS690 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (PCI Express Port 1)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB600 Non-Raid-5 SATA
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI0)
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI1)
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI2)
00:13.3 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI3)
00:13.4 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI4)
00:13.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB Controller (EHCI)
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB600 IDE
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB600 PCI to LPC Bridge
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS690M [Radeon X1200 Series]
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
schrummy@Schrummy:~$ ^C
schrummy@Schrummy:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 
```

```
schrummy@Schrummy:~$ sudo lshw -class network
[sudo] password for schrummy: 
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
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
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.2.8 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:21 memory:fe5fe000-fe5fffff
  
```

3. Mediacom is my provider [united States]

4. ```
 schrummy@Schrummy:~$ uname -a
Linux Schrummy 3.2.0-32-generic-pae #51-Ubuntu SMP Wed Sep 26 21:54:23 UTC 2012 i686 athlon i386 GNU/Linux
 
```

```
 schrummy@Schrummy:~$ uname -a
Linux Schrummy 3.2.0-32-generic-pae #51-Ubuntu SMP Wed Sep 26 21:54:23 UTC 2012 i686 athlon i386 GNU/Linux
schrummy@Schrummy:~$ ^C
schrummy@Schrummy:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.1 LTS
Release:    12.04
Codename:    precise
 
```

7. ```
  schrummy@Schrummy:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:23:a7:63:d6  
          inet addr:192.168.2.8  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:fea7:63d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1223 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2068570 (2.0 MB)  TX bytes:149629 (149.6 KB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11327 (11.3 KB)  TX bytes:11327 (11.3 KB)

```

```
schrummy@Schrummy:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.  
```

```
 schrummy@Schrummy:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
 
```

```
 schrummy@Schrummy:~$ ping -c 3 208.67.219.101
PING 208.67.219.101 (208.67.219.101) 56(84) bytes of data.

--- 208.67.219.101 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2015ms

schrummy@Schrummy:~$ ping -c 3 216.239.51.99
PING 216.239.51.99 (216.239.51.99) 56(84) bytes of data.

--- 216.239.51.99 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2014ms
 
```

```
  schrummy@Schrummy:~$ ping -c 3 www.opendns.com
PING www.opendns.com (67.215.92.210) 56(84) bytes of data.
64 bytes from 67.215.92.210: icmp_req=1 ttl=51 time=77.7 ms
64 bytes from 67.215.92.210: icmp_req=2 ttl=51 time=78.2 ms
64 bytes from 67.215.92.210: icmp_req=3 ttl=51 time=78.6 ms

--- www.opendns.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 77.766/78.220/78.611/0.474 ms
 
```

---

### Post by schrummy on 2012-11-10
lsusb and lshw -class network were messed up.... here they are

```
 schrummy@Schrummy:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 
```


```
 schrummy@Schrummy:~$ sudo lshw -class network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
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
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.2.8 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:21 memory:fe5fe000-fe5fffff
  
```

---

### Post by den_ on 2012-11-11
Ok, you have a Broadcom chip, so I supose you need to use a proprietary driver for it.

---

### Post by den_ on 2012-11-11
For the case you are not sure how to do that, type software sources in dash and go to 'Additional drivers' tab.

---

### Post by den_ on 2012-11-11
Sorry, I have just noticed that driver being used is b44. I am not sure so I am just guesing, but since the name of the card has 'BCM4311' in it, maybe you should try using b43 driver?

[Install Broadcom b43 and b43-legacy wireless driver in Ubuntu 12.10 / 12.04]("http://www.howopensource.com/2012/10/install-broadcom-b43-legacy-wireless-driver-in-ubuntu-12-10-12-04/")

---

### Post by ugm6hr on 2012-11-12
Read this:
[http://askubuntu.com/questions/139168/dell-1390-wireless-bcm4311-ubuntu-12-04-no-wireless-icon-in-unity](http://askubuntu.com/questions/139168/dell-1390-wireless-bcm4311-ubuntu-12-04-no-wireless-icon-in-unity)

The issue is with the BCM wifi cards, the driver options are either wl or b43. Some work better with 1 than other (I have a BCM4312 which is better with wl).

However, it appears that combing this with a wired BCM card that uses b44 driver complicates things further.

My suggestion:
1.Reinstall b43:
```
sudo apt-get update
sudo apt-get install firmware-b43-installer
sudo apt-get remove bcmwl-kernel-source
```
reboot

Still not working?
> To that end, I blacklisted 'wl'. Once that was done, I added 'b43' to /etc/modules, and the 'b43' driver then loaded automatically at startup, and everything worked smoothly.

---

