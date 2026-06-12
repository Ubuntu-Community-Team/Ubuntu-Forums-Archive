---
title: "Problem with Ethernet on Inspiron notebook"
date: 2011-02-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by LeftWIngPenguin on 2011-02-10
I installed the latest version of Ubuntu on a Dell Inspiron notebook. Everything seemed to be going well, but for some reason it seems to be having trouble connecting to the internet. I've plugged the thing into my Linksys wireless network hub, it seems to be detecting something (Which it calls ETH 0), but when I try to connect it tries for several minutes and then gives up. I thought it might be because I needed to enter the network password, but I can't find anywhere to do so. Can someone help me?

---

### Post by P4man on 2011-02-10
Im assuming the router and network cable work fine with another PC or they worked fine with windows, right?

If so, can you open a terminal (apps > accessories > terminal) and type in the following:

```
lspci 
```

That will spit out all your PCI(E) devices. Id like to see what it says exactly for ethernet controller. 

If you can copy paste the output to an USB stick (or connect wirelessly?) then also show us the output of

```
ifconfig

```

and

```
lshw -C network
```
(note the C is in uppercase, and it has to be).

---

### Post by Mainewha on 2011-02-10
Actually I was wondering the same thing

---

### Post by LeftWIngPenguin on 2011-02-10
Here are the results of the commands you wanted me to run: 

> lspci:

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
03:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
03:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller
03:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


ifconfig

eth0      Link encap:Ethernet  HWaddr 00:11:43:7b:22:9c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8304 (8.3 KB)  TX bytes:8304 (8.3 KB)


lshw -C network

  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:11:43:7b:22:9c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.110 firmware=5751-v3.29a latency=0 multicast=yes
       resources: irq:16 memory:dfcf0000-dfcfffff
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:dfbfe000-dfbfffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:da:54:30
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-22-generic firmware=N/A multicast=yes wireless=IEEE 802.11bg


Is there anywhere I can learn what all this stuff means?

---

### Post by P4man on 2011-02-10
> **LeftWIngPenguin said:**
> 
Is there anywhere I can learn what all this stuff means?

Heh. No idea. Keep reading here and you'll learn much of it. Let me tell you what I was looking for. lspci lists all PCI devices, and this one is what I wanted to see:

*Ethernet controller: Broadcom Corporation NetXtreme BCM5751 *

That is your network controller chipset. AFAICT, it doesnt need any additional drivers. It should just work.

The ifconfig command gives information about the network interfaces. eth0 is your wired network interface, and its "up" seems to be working, it also gets the hardware MAC address,  but its not getting an IP address and if I read it right, its not detecting its actually connected to anything, otherwise you would see "RUNNING" in there, I think.

But since Im not entirely sure, lets see what it does when you tell the network card to obtain an IP address. Run this in a terminal:

```
sudo dhclient eth0
```

And post the output here.

But TBH, at this point, Im guessing its simply a bad cable or a problem with the router/hub. Can you try another cable or connect another machine to the same cable? Also can you check the back of your pc, if plug the cable in, do you see a LED changing color? Unplugging/resetting the router or hub might also help.

---

### Post by LeftWIngPenguin on 2011-02-10
This is what I get:

```
Listening on LPF/eth0/00:11:43:7b:22:9c
Sending on   LPF/eth0/00:11:43:7b:22:9c
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.2.106 from 192.168.2.1
DHCPREQUEST of 192.168.2.106 on eth0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.2.106 on eth0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.2.106 on eth0 to 255.255.255.255 port 67

```

and then it repeats the last five lines ad infinitum without stopping. I checked the Ethernet cable, and both LEDs are lighting up on the back.

---

### Post by P4man on 2011-02-10
Hmm.. interesting. And this is almost getting above my pay grade :)

From what I understand, your network card discovers your DHCP server (192.168.2.1, which would be your router I assume), requests an IP address and is offered one, but the DHCP server (your router) is not acknowledging it? Seems like a crappy router.

Lets try manually configuring that IP address. And lets use a GUI for a change.

 Right click the network icon in the system tray (top right) and select "edit connections". In Wired, select ADD.
Give the connection a meaningful connection name, go to IPv4 settings, select Manual method. Now add an IP address:
```
192.168.2.106 
```(press ENTER to go to Netmask field)
Under netmask enter
```
255.255.255.0
``` (question to others, is "24" the same?) and press ENTER again
under gateway enter
```
192.168.2.1
```

In DNS servers, lets use google's DNS servers:
```
8.8.8.8, 8.8.4.4
```
You can also use 192.168.2.1 if you want to use your ISP's DNS servers, but google is pretty fast.

You can leave search domains empty.
Perhaps check make available to all users. 

Should look like this:

[[IMG]http://img651.imageshack.us/img651/8711/screenshoteditingstatic.png[/IMG]](http://img651.imageshack.us/i/screenshoteditingstatic.png/)

Oh and perhaps click "connect automatically"

Click apply.

Then from the network manager icon, left click it and select your new connection.  See if you are now online.

---

### Post by LeftWIngPenguin on 2011-02-10
Okay, so I did that and got the "connected" message with no problem. Still can't access any webpages though. Weird. :confused:

---

### Post by P4man on 2011-02-10
Okay, can you try clicking this link?

[http://74.125.77.99/](http://74.125.77.99/)

If that gives you google homepage, then you have a DNS problem. 
But I suspect it wont, in which case, give us the output again of

```
ifconfig
```

Now that you are "connected".

and try pinging your router 10x:

```
ping -c 10 192.168.2.1
```

If that actually works, then there is routing problem. Go to system > administration > network tools > traceroute

Try tracing [www.google.com](www.google.com). See where it ends. Alternatively, do it from a command line so you can copy paste the output:
```

sudo apt-get install traceroute
tracert 71.125.77.99
```

---

### Post by LeftWIngPenguin on 2011-02-11
Alright, so here's what happened. Navigating to [http://74.125.77.99/](http://74.125.77.99/) didn't do any better than using [www.google.com](www.google.com).

Pinging my router gets me 10 pings, no problem.

It won't let me install traceroute using Terminal--tells me there's no such package available.

When I used traceroute through network tools, [www.google.com](www.google.com) it didn't do anything-grayed out the window for a while then returned a message that no such location exits. When I tried to trace [http://74.125.77.99/](http://74.125.77.99/), it returned some information--apparently it didn't get past ubuntu-laptop.local.

This is really strange. It didn't give me half this many problems when I tried installing Ubuntu on a partition on my Mac mini.

---

### Post by LeftWIngPenguin on 2011-02-11
Also, I tried manually downloading and installing the wireless drivers for my broadcom wireless card. It says the driver is installed, but when I go to the wireless icon at the top of the screen, it still tells me the firmware is missing.

---

### Post by P4man on 2011-02-11
Can you post the output of ```
ifconfig
``` again, now that you are "connected" ? Also the output of 

```
route
```

Fixing wireless will probably be easy once we get wired working.

---

### Post by LeftWIngPenguin on 2011-02-11
Incidentally, I just realized that it's not an Inspiron, it's a Latitude. D810. Don't know why I was thinking otherwise.

---

### Post by LeftWIngPenguin on 2011-02-11
```
ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:11:43:7b:22:9c  
          inet addr:192.168.2.106  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:fe7b:229c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1001 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1242 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:91373 (91.3 KB)  TX bytes:93233 (93.2 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:980 errors:0 dropped:0 overruns:0 frame:0
          TX packets:980 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:90694 (90.6 KB)  TX bytes:90694 (90.6 KB)

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
```

Note that that last line: default appeared after a short pause.

---

### Post by P4man on 2011-02-11
That all looks perfectly ok. And since you can ping the router, but not get anywhere beyond it, it looks like a problem with the router. What sort of router is it? Can you try resetting it?

---

### Post by LeftWIngPenguin on 2011-02-11
Hmm, fair enough. It's a Linksys wireless router--we've been using it for a long time with no problem. The wireless is working fine, at any rate, but I'll try and see if resetting it helps.

Thanks

---

