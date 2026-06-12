---
title: "Internet not working."
date: 2008-12-22
forum: General Help
---

### Post by retskrad on 2008-12-22
I juts installed ubuntu with Wubi and logged in. then I realise iternet isnt working. Suddenly it sayd disconected when connecting to internet. Last time I installed wubu internet worked.
When I right click on the internet thing at the right top, it says Auto eth0 or something, I clicked on it and the internet loads again. Thenn again it says disconected. I have tried amny times to restart. Internet works in windows, but not in ubuntu. Whats going on?


PS:I'm using ubuntu 8.10.

EDIT: I wrote ifconfig in the terminal and I got this and burned it to a dvd and logged into windows to show you guys:

> admin3@ubuntu:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:11:09:6c:cd:5e
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:23 Base address:0xa000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:240 errors:0 dropped:0 overruns:0 frame:0
TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:15040 (15.0 KB) TX bytes:15040 (15.0 KB)

admin3@ubuntu:~$


I also tried installing Kubuntu, still I don't have internet. Then, now I tried Mythbuntu, still no internet.
The weird thing is that when I login to windows, internet IS working.

Can anyone help me?

---

### Post by retskrad on 2008-12-22
Anyone?

---

### Post by retskrad on 2008-12-22
Bump

---

### Post by jonobr on 2008-12-22
looks like your not getting an ip address assigned to you, or you are not defining one if its static

What does your router your connecting to expect?
is it DHCP or static?

If its dhcp then ifconfig eth0 down
ifconfig eth0 up
check Ifconfig between them.

Also, recommend a bit more time between bumps,

---

### Post by retskrad on 2008-12-22
It says its DHCP .  believe.

Also I bump the thrwad because nobody answears, I also tried wit othet forums, nobdy answears. Whats going on.. why dd it work before and not now? Why does it work in windows but not in ubuntu, kubuntu, mythbuntu=?

---

### Post by retskrad on 2008-12-22
Bump

---

### Post by retskrad on 2008-12-22
bump

---

### Post by albinootje on 2008-12-22
> **retskrad said:**
> I juts installed ubuntu with Wubi and logged in. then I realise iternet isnt working. Suddenly it sayd disconected when connecting to internet. Last time I installed wubu internet worked.

Can you post the output of :
```

lshw -c Network
lspci
ifconfig -a
sudo dhclient
ping -c 3 62.108.1.65

```

---

### Post by monkeyking on 2008-12-22
also try posting your

/etc/network/interfaces

---

### Post by retskrad on 2008-12-22
am i supposed to write those lines in the terminal in order?

---

### Post by albinootje on 2008-12-22
> **retskrad said:**
> am i supposed to write those lines in the terminal in order?

Yes, please.
Hit the <enter> key after each line.
Thanks.

---

### Post by retskrad on 2008-12-22
Thanks for the reply man. i'll just remove mythbuntu and install ubuntu.

---

### Post by networm1230 on 2008-12-22
> **retskrad said:**
> I juts installed ubuntu with Wubi and logged in. then I realise iternet isnt working. Suddenly it sayd disconected when connecting to internet. Last time I installed wubu internet worked.
When I right click on the internet thing at the right top, it says Auto eth0 or something, I clicked on it and the internet loads again. Thenn again it says disconected. I have tried amny times to restart. Internet works in windows, but not in ubuntu. Whats going on?


PS:I'm using ubuntu 8.10.

EDIT: I wrote ifconfig in the terminal and I got this and burned it to a dvd and logged into windows to show you guys:


I also tried installing Kubuntu, still I don't have internet. Then, now I tried Mythbuntu, still no internet.
The weird thing is that when I login to windows, internet IS working.

Can anyone help me?


um.. last resort wipe your hard drive and start a clean install. look at your cables or call you ISP. warning do not run commends that you are not shore of some commends are dangers to your PC

---

### Post by retskrad on 2008-12-22
I wrote in the terminal:

> lshw -c Network
lspci
ifconfig -a
sudo dhclient
ping -c 3 62.108.1.65

[B]then the terminal displayed:
[/B]

> admin3@ubuntu:~$ lshw -c Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: eth0
       version: 10
       serial: 00:11:09:6c:cd:5e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: be:51:59:ed:0d:0f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
admin3@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV535 [Radeon X1650 Series] (rev 9e)
01:00.1 Display controller: ATI Technologies Inc RV535 [Radeon X1650 Series] (rev 9e)
02:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0d.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
admin3@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:11:09:6c:cd:5e  
          inet6 addr: fe80::211:9ff:fe6c:cd5e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:222 errors:0 dropped:0 overruns:0 frame:0
          TX packets:222 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13904 (13.9 KB)  TX bytes:13904 (13.9 KB)

pan0      Link encap:Ethernet  HWaddr be:51:59:ed:0d:0f  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

admin3@ubuntu:~$ sudo dhclient
[sudo] password for admin3: 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/pan0/be:51:59:ed:0d:0f
Sending on   LPF/pan0/be:51:59:ed:0d:0f
Listening on LPF/eth0/00:11:09:6c:cd:5e
Sending on   LPF/eth0/00:11:09:6c:cd:5e
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
admin3@ubuntu:~$ ping -c 3 62.108.1.65
PING 62.108.1.65 (62.108.1.65) 56(84) bytes of data.
From 169.254.6.114 icmp_seq=1 Destination Host Unreachable
From 169.254.6.114 icmp_seq=2 Destination Host Unreachable
From 169.254.6.114 icmp_seq=3 Destination Host Unreachable

--- 62.108.1.65 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 1999ms
, pipe 3
admin3@ubuntu:~$ 




---

### Post by albinootje on 2008-12-23
> **retskrad said:**
> 
description: Ethernet interface
product: RTL-8139/8139C/8139C+
vendor: Realtek Semiconductor Co., Ltd.


Thanks.

This could be helpful :
[https://answers.launchpad.net/ubuntu/+question/18140](https://answers.launchpad.net/ubuntu/+question/18140)
> 
 marcobra  said on 2007-11-21:

Try to open your /etc/rc.local

sudo gedit /etc/rc.local

and add your desired row into that file:

mii-tool -F 10baseT-HD
sudo /etc/init.d/networking restart
mii-tool -R

Please be sure, don't touch, at the end of file, the "exit 0" instruction

Hope this Help


---

### Post by retskrad on 2008-12-23
Am I supposed to write in exactly this line:

and add your desired row into that file:

> [B]mii-tool -F 10baseT-HD
sudo /etc/init.d/networking restart
mii-tool -R[/B]

Or do I need to put anything else? It says what you desire...

---

### Post by retskrad on 2008-12-23
When I write in:


"mii-tool -F 10baseT-HD
sudo /etc/init.d/networking restart
mii-tool -R"

in the terminal, it says:

"You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."

What should I do?

I troed to write in "sudo /etc/init.d/networking restart" in the terminal, the terminal then displayed:


"admin3@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
admin3@ubuntu:~$ 
"
What should I do? Whats going 0n here?!

---

### Post by albinootje on 2008-12-23
> **retskrad said:**
> When I write in:


"mii-tool -F 10baseT-HD
sudo /etc/init.d/networking restart
mii-tool -R"

in the terminal, it says:

"You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."


Please try this :

> 
Try to open your /etc/rc.local
```

sudo gedit /etc/rc.local

```
and add your desired row into that file:

mii-tool -F 10baseT-HD
sudo /etc/init.d/networking restart
mii-tool -R

Please be sure, don't touch, at the end of file, the "exit 0" instruction


---

