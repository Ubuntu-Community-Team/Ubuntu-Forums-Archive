---
title: "Latitude D500"
date: 2010-08-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Planetes on 2010-08-10
I've tried installing on this machine before unsuccessfully. What version would you recommend for the best chance of success. 

Also any tips pertaining to drivers would be much appreciated. I believe it has a broadcom chipset, if i used the right terminology there.

---

### Post by mörgæs on 2010-08-11
Please give us some specifications on the machine.

---

### Post by Planetes on 2010-08-12
Okay so i have installed karmic koala on my dell lat. d500
I have followed a few different instructions for ndiswrapper but to no avail. I "believe" i have a wireless miniPCI network card.

I don't pretend to know anything about anything so I'll thank you for your patience.

---

### Post by mörgæs on 2010-08-13
Please post the relevant output from **hwinfo**. I am not on Ubuntu right now, but I guess it is 

```
hwinfo --netcard
``` 
and 
```
hwinfo --wlan
```

I assume you used a wired internet connection while installing.

---

### Post by Planetes on 2010-08-13
No i could not connect to the internet through a LAN connection. I am currently dual booting Ububntu/Win7 on another laptop.

The HWINFO package wasn't installed so i download and installed it and it's dependency.
For hwinfo --netcard i got..
```
    [FONT=&quot]23: PCI 103.0: 0282 WLAN controller                             
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_14e4_4320
  Unique ID: y9sn.METla+0xbK4
  Parent ID: 6NW+.+ISWpD3pbdC
  SysFS ID: /devices/pci0000:00/0000:00:1e.0/0000:01:03.0
  SysFS BusID: 0000:01:03.0
  Hardware Class: network
  Model: "Dell TrueMobile 1300 WLAN Mini-PCI Card"
  Vendor: pci 0x14e4 "Broadcom"
  Device: pci 0x4320 "BCM4306 802.11b/g Wireless LAN Controller"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x0001 "TrueMobile 1300 WLAN Mini-PCI Card"
  Revision: 0x02
  Driver: "b43-pci-bridge"
  Driver Modules: "ssb"
  Device File: wlan0
  Features: WLAN
  Memory Range: 0xfcffe000-0xfcffffff (rw,non-prefetchable)
  IRQ: 5 (2322 events)
  HW Address: 00:90:4b:14:4b:2e
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11 12 13 14
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462 2.467 2.472 2.484
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "pci:v000014E4d00004320sv00001028sd00000001bc02sc80i00"
  Driver Info #0:
    Driver Status: ssb is active
    Driver Activation Cmd: "modprobe ssb"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #17 (PCI bridge)

24: PCI 108.0: 0200 Ethernet controller
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_103d
  Unique ID: rBUF.qseO3o8SOs1
  Parent ID: 6NW+.+ISWpD3pbdC
  SysFS ID: /devices/pci0000:00/0000:00:1e.0/0000:01:08.0
  SysFS BusID: 0000:01:08.0
  Hardware Class: network
  Model: "Intel 82801DB PRO/100 VE (MOB) Ethernet Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x103d "82801DB PRO/100 VE (MOB) Ethernet Controller"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x2002 
  Revision: 0x81
  Driver: "e100"
  Driver Modules: "e100"
  Device File: eth0
  Memory Range: 0xfcffd000-0xfcffdfff (rw,non-prefetchable)
  I/O Ports: 0xecc0-0xecff (rw)
  IRQ: 11 (112987 events)
  HW Address: 00:0b:db:d8:bc:33
  Link detected: no
  Module Alias: "pci:v00008086d0000103Dsv00001028sd00002002bc02sc00i00"
  Driver Info #0:
    Driver Status: e100 is active
    Driver Activation Cmd: "modprobe e100"
  Driver Info #1:
    Driver Status: eepro100 is not active
    Driver Activation Cmd: "modprobe eepro100"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #17 (PCI bridge)
[/FONT]
  
```

I only received a usage error for --wlan0

---

### Post by mörgæs on 2010-08-14
Good, I assume then that you have installed all bug fixes. 

You have a BCM4306 card. There have been a lot of questions in the fora about these cards, and most often the problem is easy to fix. I don't have the card myself, so I can not give a detailed description, but Google can :-)

---

### Post by Planetes on 2010-08-14
Alrighty i'll have a look thank you.

---

