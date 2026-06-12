---
title: "How to enable WIFI"
date: 2010-11-06
forum: Desktop Environments
---

### Post by GodsDead on 2010-11-06
I have a really old machine, that im running a live DVD of LUbuntu on, and before i install i need to make sure the Wifi works!
its connected to ethenet now, to send this message ;p

I ran some commands in the terminal that might be needed to diagnose the drivers needed to activate the PCI Wifi card, please can someone tell me how to get this working :)

Thanks in advanced Ubuntu community!

```

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82810E DC-133 (GMCH) Graphics Memory Controller Hub (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 05)
01:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
01:05.0 Ethernet controller: Digital Equipment Corporation DECchip 21142/43 (rev 30)
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 044: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler
Bus 001 Device 003: ID 0a81:0101 Chesen Electronics Corp. Keyboard
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0 UNCLAIMED   
       description: Network controller
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64
       resources: memory:efdfc000-efdfdfff memory:efdc0000-efddffff
  *-network:1
       description: Ethernet interface
       product: DECchip 21142/43
       vendor: Digital Equipment Corporation
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: eth0
       version: 30
       serial: 00:00:e8:58:f8:7d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master rom ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=192.168.0.4 latency=64 maxlatency=40 mingnt=20 multicast=yes
       resources: irq:21 ioport:cc80(size=128) memory:efdfff80-efdfffff memory:efd80000-efdbffff
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:e8:58:f8:7d  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::200:e8ff:fe58:f87d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1821 errors:482 dropped:0 overruns:0 frame:0
          TX packets:1416 errors:18 dropped:0 overruns:0 carrier:49
          collisions:0 txqueuelen:1000 
          RX bytes:1786100 (1.7 MB)  TX bytes:186001 (186.0 KB)
          Interrupt:21 Base address:0xcc80 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13408 (13.4 KB)  TX bytes:13408 (13.4 KB)

ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.



```

---

### Post by sikander3786 on 2010-11-06
Once internet is connected via ethernet cable, go to System > Administration > Hardware Driver/Additional Drivers and see if the drivers pop in there. If they do, you can easily activate them.

I have never used lubuntu so I mentioned the path for Ubuntu instead, however you might easily find Additional Drivers under some System menu on it.

---

### Post by GodsDead on 2010-11-06
Nope, Didn't find anything :(

---

### Post by sikander3786 on 2010-11-06
> **GodsDead said:**
> Nope, Didn't find anything :(
Hmmm. I found a guide here.

[https://help.ubuntu.com/community/WifiDocs/Driver/acx111](https://help.ubuntu.com/community/WifiDocs/Driver/acx111)

---

### Post by godspeedmav on 2010-11-09
Additional Drivers can be found at click the Menu icon > Preferences > Additional Drivers.

And Yes, I found the same guide for wifi: [https://help.ubuntu.com/community/WifiDocs/Driver/acx111](https://help.ubuntu.com/community/WifiDocs/Driver/acx111) :)

---

### Post by cavalier911 on 2010-11-09
**Lubuntu 10.4 LTS**

Install:

ndisgtk - graphical frontend for ndiswrapper (installation of Windows WiFi drivers)
 
Menu/Preferences/Windows Wireless Drivers


```
00:0d.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
	Subsystem: ZyXEL Communication Corporation Device 340b
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 10
	Region 0: Memory at f4008000 (32-bit, non-prefetchable) [size=8K]
	Region 1: Memory at f4020000 (32-bit, non-prefetchable) [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: **ndiswrapper**


```
```
 *-network
             description: Wireless interface
             product: ACX 111 54Mbps Wireless Interface
             vendor: Texas Instruments
             physical id: d
             bus info: pci@0000:00:0d.0
             logical name: wlan0
             version: 00
             serial: 00:13:49:54:2a:b5
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=ndiswrapper+tnet1130 driverversion=1.55+ZyXEL,12/01/2004,7.0.1.33 ip=192.168.123.3 latency=64 multicast=yes wireless=IEEE 802.11g
             resources: irq:10 memory:f4008000-f4009fff memory:f4020000-f403ffff

```

```
rj@lubuntu:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
tnet1130 : driver installed
	device (104C:9066) present

```

---

### Post by Texasdad on 2010-11-09
I cannot activate Medialink USB N adapter Model no. MWN-USB150N to work with my Ubuntu 10.10--- I have tried downloading Windows wioreless drivers, Wicd network manager , did an iwconfig and got the following results:
I would appreciate your help 



desktopChess:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     Ralink STA  ESSID:""  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=70/100  Signal level:0 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by cavalier911 on 2010-11-09
I have a tenda w311u wireless which may have the same chip.
This works on Lubuntu 10.4 LTS with network manager
Run the lsusb command in terminal if what's in bold below matches do the following to activate the adapter.
```
rj@lubuntu:~$ lsusb
Bus 002 Device 003: ID **148f:3070** Ralink Technology, Corp. 

```

```
sudo nano /etc/modprobe.d/blacklist.conf
```

Add this to bottom:
```

blacklist rt2800usb
blacklist rt2x00usb

```

Reboot

Google search ubuntu wireless with your wireless adapters ID code if it's different.

---

