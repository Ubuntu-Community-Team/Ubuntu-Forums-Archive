---
title: "Wifi Frustration - Starting to hate Ubuntu"
date: 2010-12-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by DojoMouse on 2010-12-16
My wifi card and Ubuntu don't seem to be getting along.  I've searched and searched this forum and have tried several fixes and none have worked for more than 24 hours.  

I have a Dell Inspiron Mini 10 with the latest Ubuntu (Natty Narwhal) loaded as the sole operating system.  My computer can SEE wireless networks, but simply cannot obtain an IP address from any of them.

> **lspci**
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
03:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

> **lsusb**
Bus 005 Device 004: ID 04e8:663e Samsung Electronics Co., Ltd D900e Phone
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 413c:02b0 Dell Computer Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 002: ID 064e:a129 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

> **lshw -class network**
 *-network               
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:25:56:6b:e9:b3
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:24:e8:c1:9b:30
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.2.4 latency=0 multicast=yes
       resources: irq:43 ioport:2000(size=256) memory:f0510000-f0510fff memory:f0500000-f050ffff memory:f0520000-f053ffff

We have comcast.  I am currently connecting to the internet through ethernet to a Belkin Wireless G router.  I would love to be connecting to the same wirelessly.  Sadly Ubuntu does not seem able or up to making this happen.

> **ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:24:e8:c1:9b:30  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::224:e8ff:fec1:9b30/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10804548 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7923771 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3474077556 (3.4 GB)  TX bytes:3043339129 (3.0 GB)
          Interrupt:43 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:25:56:6b:e9:b3  
          inet6 addr: fe80::225:56ff:fe6b:e9b3/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:12333 errors:23071 dropped:0 overruns:0 frame:2154415
          TX packets:9391 errors:574 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4971279 (4.9 MB)  TX bytes:4811468 (4.8 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3446 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3446 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:270312 (270.3 KB)  TX bytes:270312 (270.3 KB)

> **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:199
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

> **route -n**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.1     0.0.0.0         255.255.255.255 UH    0      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0

> **ping -c 3 208.67.219.101i**
PING 208.67.219.101 (208.67.219.101) 56(84) bytes of data.

--- 208.67.219.101 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2016ms


My router is currently unencrypted (which annoys me to no end) and I still cannot connect to it.  What the hell is happening?  Anyone?

---

### Post by DojoMouse on 2010-12-16
I should also mention that I am a total Ubuntu N00b, so please be very explanatory in your answers - also, both of my housemates' pcs and my wii work just fine with the router at present.

---

### Post by mickwombat on 2010-12-16
Understand the frustration.  Let's try a couple of things to get it working.

> My wifi card and Ubuntu don't seem to be getting along. I've searched and searched this forum and have tried several fixes and none have worked for more than 24 hours. 

Do you mean that it was working before?  Have you tried a live cd to see if it works with that?

I find the network-manager applet to be a pile of poo.  Install the application wicd.  Somewhere you should be able to specify to use eth1, which looks like your wireless card.

If that works, then stop network-manager, which you can do by

```
sudo service network-manager stop
```

Post back how you got on

:D

---

### Post by PRC09 on 2010-12-16
> I have a Dell Inspiron Mini 10 with the latest Ubuntu (Natty Narwhal) loaded as the sole operating system. My computer can SEE wireless networks, but simply cannot obtain an IP address from any of them.

Not trying to be a smart a** here but mentioning that you are a noob using a testing version of an operating system has all the makings of a very frustrating experience......The next round of updates Could undo everything and you are back at the start again......

---

### Post by amsterdamharu on 2010-12-16
>  have worked for more than 24 hours
This would suggest that you have switched it on. I actually went back to the store with my laptop because windows could see the wireless (the hardware) but never found the router/available network. Even went walking around an area that had shops providing wireless services but never picked up anything. Turns out that I have to press fn + F3 to switch it on. After a big DUH... it worked fine with both Linux and Windows but have to switch it on every time I start.

---

### Post by amsterdamharu on 2010-12-16
> **PRC09 said:**
> Not trying to be a smart a** here but mentioning that you are a noob using a testing version of an operating system has all the makings of a very frustrating experience......The next round of updates Could undo everything and you are back at the start again......

That is an excellent point, you should install 10.04 it's the long term supported Ubuntu or if you want to watch youtube and listen to mp3 without too much tweaking (you're not in the US or Japan) then get Linux Mint 9.

---

### Post by DojoMouse on 2010-12-16
> **mickwombat said:**
> Understand the frustration.  Let's try a couple of things to get it working.



Do you mean that it was working before?  Have you tried a live cd to see if it works with that?

I find the network-manager applet to be a pile of poo.  Install the application wicd.  Somewhere you should be able to specify to use eth1, which looks like your wireless card.

If that works, then stop network-manager, which you can do by

```
sudo service network-manager stop
```

Post back how you got on

:D

Apologies for the n00b question, and I understand the few disparaging responses that I got, but I didn't know I was beta testing an OS.  My apologies.  That said...

This worked like a** frikken charm**.  I am currently posting off of my wireless router.  So simple.  Thank you.  Thank you so much.

I already had WiCD Network Manager installed, but had no idea how to let it have free rein over my wireless card.  Basically, I was able to see a whole lot of information about the networks that I was unable to connect to.  That 
'sudo service network-manager stop'
 command made it go.  I will check back in periodically if it seems it is intermittent, but, seriously, **instafix**.  Thank you again.

*Edit: This will disable the "connected notifier" in the upper right hand corner of your screen.  You'll show disconnected.  Doesn't matter at all.  Mine currently shows a giant red exclamation point through the radiating arcs, and I'm posting this.  Wirelessly.  Ignore it.*

---

### Post by mickwombat on 2010-12-16
Didn't read properly the above posts.  You really shouldn't be using 11.04 version of Ubuntu as others quite rightly said.  Sounds like you're just starting out anyway, and I would suggest reinstalling with 10.04.....you'll save loads of headaches....and time in the end. ;)

> This will disable the "connected notifier" in the upper right hand corner of your screen. You'll show disconnected. Doesn't matter at all. Mine currently shows a giant red exclamation point through the radiating arcs, and I'm posting this. Wirelessly. Ignore it.

That icon is for network-manager, and as it was stopped, this is normal.  You can disable from startup by going to System-Preferences-Startup Applications and unchecking.  I have a little icon for wicd, but can't remember if that was put there automatically or something I did.

I'd suggest installing netspeed-applet and adding to your panel at top.  It's a nice, basic little applet that shows your current up/down load speed.

Glad you got it sorted.  Happy learning.

=D>

---

### Post by frank0936 on 2011-01-01
Where do you find this WCID? I went to Get software and typed wcid in the search box and I get 0 matching items.
Frank

---

### Post by Hakunka-Matata on 2011-01-01
> **frank0936 said:**
> Where do you find this WCID? I went to Get software and typed wcid in the search box and I get 0 matching items.
Frank
[http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")


WICD

---

### Post by frank0936 on 2011-01-01
Thank you!

---

### Post by perspectoff on 2011-01-01
Wicd is in the repositories, so you can get it through Synaptic Package Manager or KPackageKit. You can also install it from the command-line:

 sudo apt-get install wicd

But before installing it, you must remove all the network-manager associated modules and reboot once (to make sure network-manager is gone).

Of course, once you have removed network-manager, you must be connected by a wired connection to access the Internet (the Linux kernel allows wired access without any network manager whatsoever) and install wicd.

More details:

Ubuntuguide.org:
[http://ubuntuguide.org/wiki/Ubuntu:Maverick#Wicd_Network_Manager](http://ubuntuguide.org/wiki/Ubuntu:Maverick#Wicd_Network_Manager)

Kubuntuguide:
[http://kubuntuguide.org/Maverick#Wicd_Network_Manager](http://kubuntuguide.org/Maverick#Wicd_Network_Manager)

---

