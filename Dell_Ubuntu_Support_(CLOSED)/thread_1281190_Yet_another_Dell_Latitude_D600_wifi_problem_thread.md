---
title: "Yet another Dell Latitude D600 wifi problem thread"
date: 2009-10-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by meowcarrot on 2009-10-03
I just picked up a laptop to give to my brother and can't get the wifi working. It's a Dell Latitude D600 running Hardy Heron. The wifi is on, and it can see my router, but when I try to connect it doesn't work. I've added Ndiswrapper and updated the drivers... I'm at a loss.

> jonathan@helo:~$ sudo lshw -C network
[sudo] password for jonathan: 
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:a0:b5:1d
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5705-v3.16 ip=192.168.2.2 latency=32 link=yes mingnt=64 module=tg3 multicast=yes port=twisted pair speed=1GB/s
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: wlan0
       version: 04
       serial: 00:0c:f1:1e:ce:c3
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+w70n51 driverversion=1.52+Intel,10/11/2003,1.2.1.3 latency=32 link=no maxlatency=34 mingnt=2 module=ndiswrapper multicast=yes wireless=IEEE 802.11b
>  iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID: Off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   
          RTS thr=1600 B   Fragment thr=2344 B   
          Power Management: Off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


>  ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:1f:a0:b5:1d  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:fea0:b51d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:97914 errors:0 dropped:0 overruns:0 frame:0
          TX packets:73959 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:145787475 (139.0 MB)  TX bytes:5843282 (5.5 MB)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1786 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1786 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:89300 (87.2 KB)  TX bytes:89300 (87.2 K

wlan0     Link encap:Ethernet  HWaddr 00:0c:f1:1e:ce:c3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:722 (722.0 B)  TX bytes:9128 (8.9 KB)
          Interrupt:5 Memory:fafef000-faff0000 
Any ideas?

---

### Post by urugTON on 2009-10-03
I have a Dell Latitude D610 which is running wireless fine on Jaunty.  It uses a PRO/Wireless 2200BG [Calexico2] from Intel and not what you have.  I too got an older laptop, but mine has only run 9.04 - Jaunty.

I will note that I have another Dell laptop, a Vostro 1510.  I originally ran it with Hardy - 8.04.  I had to back port drivers and switch to Wicd in order to get wireless running on 8.04.  The Vostro has run wireless 8.10 & 9.04 off the LiveCD.  I'd suggest burning a 9.04 LiveCD and trying that.

My attempts at using 8.04 with Ndiswrapper were very frustrating and completely fruitless on the Vostro.  Fortunately I've not had any issues with either laptop's wireless on 9.04.

Good luck.

---

### Post by mikewhatever on 2009-10-04
Intel's wireless cards don't need ndiswrapper because they mostly work out of the box, regardless, there is an ip address under the wireless interface, which means that you are connected to the router.

---

### Post by lswb on 2009-10-04
Your ifconfig post shows that you are connected to a network through your wired ethernet interface eth0. Network Manager will not connect to wireless when a wired network is available. Try disconnecting the ethernet cable and see what happens.

---

### Post by meowcarrot on 2009-10-06
ifconfig showed a wired connection because I had run it while writing the post, which required an internet connection. :) The answer in the end was upgrading to Intrepid. 

As I mentioned in OP, the laptop could see my router as a wireless network to join without issue, but it wasn't connecting. Weird thing is, now my Inspiron 640m running Jaunty is doing the same thing >.> I wonder if my router is being cranky... (linksys WRT54GL). Anyway, this is as resolved as it's going to get as I no longer have access to the laptop.

---

