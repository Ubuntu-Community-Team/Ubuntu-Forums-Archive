---
title: "No Wired Network Connection"
date: 2011-09-02
forum: Desktop Environments
---

### Post by squared2 on 2011-09-02
Been fighting with this for a few hours now and getting very agitated.

Computer: 
Core 2 Duo Extreme Quad qx6700 2.6ghz. 
4GB DDR2 RAM.
nVidia GeForce 9800 GT
150GB WD SATA Drive (all my other drives are currently disconnected).
And for some reason, my motherboard box is MIA...

The Short:
Windows 7 installed on computer. I decided I wanted to try out this 11.04 (I haven't used ubuntu in a very long time). Downloaded and installed along-side Windows 7 (dual boot).

Now, my motherboard has 2 ethernet ports built in. I only ever use 1 in Windows, so I recorded the MAC and its relevant information before switching over to ubuntu.

Boot into ubuntu. Not getting any internet connectivity. I try using the Connection Manager to manually set ipv4 settings and toggling ivp6 from Ignore, Automatic. Nothing is working. I notice the MAC ID is different from one I use. Check Network Tools and it gives eth0 and eth1. eth0 seems to be the only "usable" one through the connection manager. According to the MAC, eth1 is the one I use in Windows.

eth0 is not the one I was using, so I get an extra cable and just plug it in anyway to see if that will work. Rebooting, ifup eth0, nothing is connecting it.

Even went into the bios and turned on Post ethernet checks for both lans.

Here are some printouts of what I am currently at.

lspci
```
squared@squared-System:~$ lspci
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:06.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:13.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:14.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:15.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:16.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:17.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GT] (rev a2)
04:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
08:00.0 Mass storage controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
```

lspci | grep Ethernet
```
squared@squared-System:~$ lspci | grep Ethernet
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
```

ifconfig
```
squared@squared-System:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:92:c9:1c:9b  
          inet6 addr: fe80::21a:92ff:fec9:1c9b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4071 (4.0 KB)
          Interrupt:49 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:1a:92:c9:25:b0  
          inet6 addr: fe80::21a:92ff:fec9:25b0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3799 (3.7 KB)
          Interrupt:50 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9024 (9.0 KB)  TX bytes:9024 (9.0 KB)
```

less /etc/network/interfaces
```
auto lo
iface lo inet loopback
```

I have also tried "iface eth0 inet dhcp" AND "iface eth1 inet dhcp" in interfaces.

Oh, and my setup is a Linksys WRT54GL to a Cisco DPC3000 cable router. DHCP is enabled and works just fine for Windows. No static IP is set in Windows.

When I tried static IP in the connection manager, it would say connected, but nothing worked. I wasn't pulling an ipv4 address either with ifconfig. I could only ping 127.0.0.1. Could not ping my gateway which is 192.168.1.1 or any outside address or IPs.

Thoughts?

---

### Post by squared2 on 2011-09-02
Opps, sorry. Just saw the Networking / Wireless section. Please move if needed. Sorry about that.

---

### Post by HugoSerrano on 2011-09-02
Hello!

Try, on a terminal:
> sudo dhclientRegards!

---

### Post by squared2 on 2011-09-02
> **HugoSerrano said:**
> Hello!

Try, on a terminal:
Regards!

Will give that a try. I did try sudo dhclient eth0 before and that didn't work.

I just uninstalled the network manager so it doesn't over-ride anything in interfaces. Will try it again.

---

### Post by squared2 on 2011-09-02
> **HugoSerrano said:**
> Hello!

Try, on a terminal:
Regards!

That didn't work.

Some changes I did: I removed Network Manager from the software so I only have to deal with interface.

Added dhcp to interface for both devices:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
```

ifconfig:
```
squared@squared-System:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:92:c9:1c:9b  
          inet6 addr: fe80::21a:92ff:fec9:1c9b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4515 (4.5 KB)
          Interrupt:49 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:1a:92:c9:25:b0  
          inet6 addr: fe80::21a:92ff:fec9:25b0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4515 (4.5 KB)
          Interrupt:50 Base address:0xe000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1a:92:c9:1c:9b  
          inet addr:169.254.8.17  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:49 Base address:0x4000 

eth1:avahi Link encap:Ethernet  HWaddr 00:1a:92:c9:25:b0  
          inet addr:169.254.8.158  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:50 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:224 errors:0 dropped:0 overruns:0 frame:0
          TX packets:224 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17088 (17.0 KB)  TX bytes:17088 (17.0 KB)
```

Now they're both pulling IP addresses that make no sense to me. Should be assigned 192.168.100 or 101 at the end, something like that. I still can't connect. I can't ping out or my router.

I tried the "sudo dhclient", nothing. Tried "sudo dhclient eth0", nothing. Same for eth1.

---

### Post by HugoSerrano on 2011-09-02
Those IP address are normal. They are assigned by your PC. Search for apipa on google to know some more.

Do you have ethtool in your pc?
> #sudo ethtool eth0This will give you something like:
> Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  Not reported
    Link partner advertised pause frame use: No
    Link partner advertised auto-negotiation: No
    Speed: 1000Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Supports Wake-on: g
    Wake-on: d
    Current message level: 0x0000003f (63)
    Link detected: yes


---

### Post by HugoSerrano on 2011-09-02
try this:

> sudo su
rmmod forcedeth
modprobe forcedeth msi=0 msix=0
/etc/init.d/networking restart

from:
[http://www.overclock.net/linux-unix/508176-how-asus-p5n32-e-sli-plus.html#post6236427](http://www.overclock.net/linux-unix/508176-how-asus-p5n32-e-sli-plus.html#post6236427)

---

### Post by squared2 on 2011-09-02
> **HugoSerrano said:**
> try this:



from:
[http://www.overclock.net/linux-unix/508176-how-asus-p5n32-e-sli-plus.html#post6236427](http://www.overclock.net/linux-unix/508176-how-asus-p5n32-e-sli-plus.html#post6236427)

Nice find, will give it a try right now. And no I don't have the ethtools. Is a fresh install, hasn't been able to connect.

---

### Post by squared2 on 2011-09-02
That was an awesome find indeed. I am posting this from my ubuntu install. :guitar:

So now I'm guessing I need to do the part where he says to make it permanent. Thank you SO much for pointing me there. I was about ready to shave the cat! :P

---

### Post by HugoSerrano on 2011-09-02
hehe :-)
Glad i could help!

Do an update first. You may get it solved just with a kernel update.

---

