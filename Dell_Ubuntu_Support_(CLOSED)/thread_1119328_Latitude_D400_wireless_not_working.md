---
title: "Latitude D400 wireless not working"
date: 2009-04-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nigelewan on 2009-04-07
I have a Dell Latitude D400 laptop with the Jaunty beta installed. Wireless does not work; no wireless networks show up under Network Manager and I can't get anything by typing in an SSID either. When I do hwinfo --wlan, I get this:
```
01: PCI 103.0: 0282 WLAN controller                             
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_8086_1043
  Unique ID: kX1R.x4JwOxzAi8D
  Parent ID: 6NW+.+ISWpD3pbdC
  SysFS ID: /devices/pci0000:00/0000:00:1e.0/0000:01:03.0
  SysFS BusID: 0000:01:03.0
  Hardware Class: network
  Model: "Intel PRO/Wireless LAN 2100 3B Mini PCI Adapter"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x1043 "PRO/Wireless LAN 2100 3B Mini PCI Adapter"
  SubVendor: pci 0x8086 "Intel Corporation"
  SubDevice: pci 0x2565 
  Revision: 0x04
  Features: WLAN
  Memory Range: 0xfcfee000-0xfcfeefff (rw,non-prefetchable)
  IRQ: 11 (no events)
  Requires: ipw-firmware
  Module Alias: "pci:v00008086d00001043sv00008086sd00002565bc02sc80i00"
  Driver Info #0:
    Driver Status: ipw2100 is not active
    Driver Activation Cmd: "modprobe ipw2100"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #11 (PCI bridge)

```

I do not understand what most of this means, but I did a Google search for 'dell 2100 driver' and found some Windows package. I downloaded it, extracted it and found an .inf file, and tried to install it with 'Windows Wireless Drivers'. When I did, I got an error that said, 'Unable to see if hardware is present.' However, when I dismissed this, the dialog said 'Hardware present: yes'. But still nothing works. I'm just very confused. I think I must be close, but I don't know what to do. Any help would be wonderful. Thanks!

---

### Post by mcjohnson on 2009-04-08
I was having the exact same problem on a different Dell. I have a dual boot with Windows, and I had to disable the powersave option. In Network Connections (In Windows), right-click the wireless connection and go to Properties. Click the Configure button, then go to the Power Management tab. Uncheck the box next to "Allow the computer to turn off this device to save power."

That got Ubuntu to recognize wireless networks, but I still can't connect to anything. When I try, it starts to connect, then asks for my username/password, then starts to connect, and repeats (and yes, I'm sure the username and password are correct). Any help would be greatly appreciated.

---

### Post by gtamplin on 2009-10-10
Apparently after getting UBUNTU to recognize the wireless NIC, it is necessary to obtain "Windows Drivers." 
That is referred to in MANY places, but NOWHERE is there EXPLICIT information on how to get them. 
I tried downloading from Microsoft, but there was no INF file, which is what the instructions say to use. 
The seeming answers are like descriptions of how to use a key to open a door, but NEVER telling where to get the key. 
Any help in locating a "Windows driver" INF file would be appreciated by me, and probably by all of the rest of us who are trying to use wireless under UBUNTU. 
I am dangerously close to digging out my old Windows XP Pro disk and going back to XP. So you can see how frustrating this months-long search has become...  
Anybody know where to get ACTUAL INF driver files for the Broadcom wireless NIC used in the Dell Latitude D400?

---

