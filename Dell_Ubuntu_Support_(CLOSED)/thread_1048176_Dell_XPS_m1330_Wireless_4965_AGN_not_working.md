---
title: "Dell XPS m1330 Wireless 4965 AGN not working"
date: 2009-01-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by chonkie on 2009-01-23
Hi,

I'm a first time poster and I've been looking through online resources to find a work around for my wireless. My computer is a Dell XPS m1330, Intel Core 2 Duo T7500 2.2 Mhz, 4 Gb RAM, Nvidia GeForce 8400M and 200 Gb HD. The wireless card is an INTEL 4965 Wireless N-MINICARD and my Access Point is care of a Billion 6404VGP connection (pre set to the default settings from MyNetFone [[www.mynetfone.com.au]](www.mynetfone.com.au]), except I had to change the DHCP settings to automatically assign an IP address as I'm using a cable modem that doesn't use PPPoE), of which likes my nintendo wii.

I've tried installing the latest windows driver off the Dell support website using the ndiswrapper as below.

Any ideas? Please help!


(please note the ndiswrapper has now been removed as I'm trying to troubleshoot)

sudo ndiswrapper -l

netw4v32 : driver installed
	device (8086:4229) present (alternate driver: iwlagn)


hwinfo --wlan

06: PCI c00.0: 0282 WLAN controller                             
  [Created at pci.310]
  UDI: /org/freedesktop/Hal/devices/pci_8086_4229
  Unique ID: y9sn.9RJazxQBVB3
  Parent ID: qTvu.TkjeLK60Af8
  SysFS ID: /devices/pci0000:00/0000:00:1c.1/0000:0c:00.0
  SysFS BusID: 0000:0c:00.0
  Hardware Class: network
  Model: "Intel PRO/Wireless 4965 AG or AGN Network Connection"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x4229 "PRO/Wireless 4965 AG or AGN Network Connection"
  SubVendor: pci 0x8086 "Intel Corporation"
  SubDevice: pci 0x1120 
  Revision: 0x61
  Driver: "iwlagn"
  Driver Modules: "iwlagn"
  Device File: wlan0
  Features: WLAN
  Memory Range: 0xf9ffe000-0xf9ffffff (rw,non-prefetchable)
  IRQ: 216 (no events)
  HW Address: 00:1d:e0:79:81:d1
  Link detected: yes
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11 36 40 44 48 52 56 60 64 149 153 157 161 165
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462 5.18 5.2 5.22 5.24 5.26 5.28 5.3 5.32 5.745 5.765 5.785 5.805 5.825
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "pci:v00008086d00004229sv00008086sd00001120bc02sc80i00"
  Driver Info #0:
    Driver Status: iwlagn is active
    Driver Activation Cmd: "modprobe iwlagn"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #19 (PCI bridge)


lspci

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)


iwconfig

lo        no wireless extensions.

eth2      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated   
          Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

### Post by compman25 on 2009-01-23
What version of Ubuntu? I have the same laptop and wifi card. Never have had to install any drivers to get it to work with 8.10.

---

### Post by chonkie on 2009-01-23
Sorry. Yeh I'm running Ubuntu 8.10, upgraded from 8.04. Could it be a setting with my router? I wouldn't think so as my Wii picked it up straight away.

---

### Post by jsternberg on 2009-01-23
My wireless also stopped working recently, although I didn't change anything (except automatic upgrades). Running 8.04 with Verizon DSL and a Westell modem, my other windows computer connects to wireless ok, so I know it's not a router problem. My Ubuntu machine sees various wireless networks, including mine, but keeps asking for hex password (although router uses WEP 138 passphrase in plain text). I see folks using Intrepid are having similar problems, but I haven't seen a fix yet, and don't know enough Linux myself. Any clues appreciated.

Ubuntu 8.04 (hardy)
2.6.24-23-generic (#1 SMP Thu Nov 27 18:44:42 UTC 2008)

i'm currently online using my ethernet connection because wireless isn't working]
*-network
description: Wireless interface
product: PRO/Wireless 3945ABG Network Connection
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:0c:00.0
logical name: wmaster0
version: 02
serial: 00:1c:bf:36:2b:c4
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
*-network
description: Ethernet interface
product: NetLink BCM5906M Fast Ethernet PCI Express
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:09:00.0
logical name: eth0
version: 02
serial: 00:1d:09:3a:ff:1e
size: 100MB/s
capacity: 100MB/s
width: 64 bits
clock: 33MHz
capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full ip=192.168.1.46 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
jsternberg is online now Report Post   	Edit/Delete Message

 iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wmaster0  no wireless extensions.
eth1      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:0E:0F:36:F0   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

 lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

---

### Post by compman25 on 2009-01-24
maybe it has to do with you having ndiswrapper driver installed. I don't have that installed and mine works with no user intervention other than giving it my WPA passphrase the 1st time.

---

### Post by chonkie on 2009-01-24
It didn't work without the ndiswrapper installed either, that's why I installed it. I might try uninstalling it later today and let you know how it goes.

I haven't set up a WPA passphrase and my Wii didn't require one so I don't think that would be the issue, right?

---

### Post by damis648 on 2009-01-24
Coincidentally enough, not five minutes ago I replaced my own 4965AGN in my M1530 with another broadcom chipset card I had lying around because my 4965 kept slowing down after 5-10 minutes of connection (just started happening). Anybody with any ideas?

---

### Post by chonkie on 2009-01-25
OK. I removed the windows driver using ndiswrapper then uninstalled ndiswrapper itself. I tried connecting to my wireless router again and it didn't pick it up. Just to be doubly sure, I've updated the firmware on the router but still nothing happened. My Wii is still loving the wireless though. Grrr.

Maybe a little more help?

---

### Post by compman25 on 2009-01-26
> **chonkie said:**
> OK. I removed the windows driver using ndiswrapper then uninstalled ndiswrapper itself. I tried connecting to my wireless router again and it didn't pick it up. Just to be doubly sure, I've updated the firmware on the router but still nothing happened. My Wii is still loving the wireless though. Grrr.

Maybe a little more help?

Is it seeing your router and just not connecting to it? I started with 8.10 and the intel 4965 worked right from the start without any work from me other than giving it my WPA passphrase.

---

### Post by chonkie on 2009-01-26
No it doesn't see my router via the wireless. When I connect the router up directly using the LAN port there's no problem, however.

---

### Post by chonkie on 2009-01-28
Hi. Can anyone else please help me out? I'm kinda getting desperate.

---

### Post by jespdj on 2009-01-30
You should not need ndiswrapper (and use a Windows driver) for the Intel 4965. The 4965 in my 1530 (with 8.04) works out-of-the-box.

---

### Post by chonkie on 2009-01-30
Hey jespdj,

I removed the ndiswrapper driver (and the software) but still no go. Do I have to keep removing my LAN cable connection to keep trying my wireless access (to avoid conflicts) or can I just try connecting with the LAN cable still plugged in?

---

### Post by PaulusT on 2009-02-02
Hi chonkie,

I have exactly the same problem I think - I can in fact see and connect to most wireless routers, but there is one (at my house) which I cannot see at all (and which is clearly working).

Could it be to do with its channel?

I don't think the Vista drivers can work with ndiswrapper. I have tried the XP drivers from the Intel website and I don't think they work either, although I am unsure how to find out - is there a way to load the drivers and assign them to the wireless card? (i.e. get an immediate success or fail message)

Also, does the:

ndiswrapper -l
netw5x32 : driver installed
	device (8086:4229) present (alternate driver: iwlagn)

...suggest that the driver is not loaded? and/or that the alternate driver is preventing the netw5x32 driver from loading?

---

### Post by ussndmac on 2009-02-02
My 1530 has the 3945 and I can see the router and it sees me, but no connection happens.

haven't found a solution.

---

### Post by PaulusT on 2009-02-03
I solved my problem:

I created a file /etc/modprobe.d/wireless

and added the line:
options lbm_cw_cfg80211 ieee80211_regdom=EU

That allows me to use channels above 11.

Hope it helps.

---

### Post by chonkie on 2009-02-06
I don't know exactly what happened but my wireless is working now. I installed startup manager (I don't think this had anything to do with it) and my laptop got accidentally hit and i had to reboot it. Wireless then started working. Weird, eh? The card might have been loosely connected into the motherboard or something. I dunno. Either way, that's one thing done. Now to post on getting Wine to play my games and my VPN (although that's probably a settings issue).

Thanks for all your help, guys.

Just one more thing. I can't set this thread to [Solved]. There's no option under thread tools. I only get:

- Show printable version
- Email this page
- Subscribe to this thread
- Add a poll to this thread

---

