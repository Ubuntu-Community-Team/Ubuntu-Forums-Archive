---
title: "LG Envy2 phone in Bitpim"
date: 2009-02-08
forum: General Help
---

### Post by 73ckn797 on 2009-02-08
Does anyone know of a way to get the LG Envy2 accessible using Bitpim? I cannot find any drivers.

---

### Post by 73ckn797 on 2009-02-10
My results here are about as productive as looking for a driver for the phone. Not surprised.

---

### Post by 73ckn797 on 2009-02-26
Bump

---

### Post by ilamythest on 2009-02-26
I have an enV2 also, and use bitpim....just open a terminal, type in sudo bitpim...enter your password. bit pim will start as root (I guess, still kinda new to this) but it will detect your phone and you can access it.
Hope this helps.

---

### Post by 73ckn797 on 2009-02-26
When I connect the phone via USB it is recognized automatically but will not configure. It does not list Verizon as a provider. I will monkey around with it some more.

---

### Post by redgs95 on 2009-06-08
i have found in another forum that you will have to purge bitpim 1.0.6 out and install 1.0.5 and lock it so it doen't upgrade. I just have to figure out how to do all of that because i have just been using ubuntu (linux) for about a week now.

---

### Post by nephlim on 2009-07-31
I had the same problem. Run bitpim as root and tell it to search for a new phone. It worked like a charm for me :)

---

### Post by ground-pilot on 2009-08-03
The phone is the LG VX9100 Env2

Using a fresh Ubuntu Jaunty install using a CSR Bluetooth USB dongle in BitPim 1.0.6 - Debian. This BitPim was installed via Jaunty - Synaptic Package Manager...

This works on Hardy just fine... So what's different. 

Ran as user and root. No device discovery. I know the device works with the system, as it does address it. OBEX hates it still. I'm working on that one. BTProximity sees the device and locks the system accordingly. It also returns the active ports sdptool finds as well. So I know that's workiing.

BitPim (as root or regular user) refuses to see or find anything.

USB Device - Vendor Cambridge Silicon Radio, Ltd, Product Bluetooth Dongle (HCI mode), (Interface #00)usb::003::008::0 This port is active but not available for use.
PropertyValueDescription [SIZE=-1]PID[/SIZE] [SIZE=-1]0x0001[/SIZE][SIZE=-1]Product ID[/SIZE] [SIZE=-1]VID[/SIZE] [SIZE=-1]0x0A12[/SIZE][SIZE=-1]Vendor ID[/SIZE] [SIZE=-1]active[/SIZE] [SIZE=-1]True[/SIZE][SIZE=-1]Your operating system shows this driver and port is correctly configured and a device attached[/SIZE] [SIZE=-1]available[/SIZE] [SIZE=-1]False[/SIZE][SIZE=-1]It was not possible to open this port[/SIZE] [SIZE=-1]description[/SIZE] [SIZE=-1]USB Device - Vendor Cambridge Silicon Radio, Ltd, Product Bluetooth Dongle (HCI mode), (Interface #00)[/SIZE]  [SIZE=-1]libusb[/SIZE] [SIZE=-1]True[/SIZE][SIZE=-1]This indicates if the usb library is in use to access this device.  Operating system             device drivers (if any) are bypassed when BitPim talks to the device[/SIZE] [SIZE=-1]name[/SIZE] [SIZE=-1]usb::003::008::0[/SIZE][SIZE=-1]This is the name the port is known to your operating system as[/SIZE] [SIZE=-1]protocol[/SIZE] [SIZE=-1]Wireless / Radio Frequency / Bluetooth[/SIZE][SIZE=-1]This is the protocol the USB device claims to speak[/SIZE]  
 Tried BitPim Com Port: usb::003::008::16

Below are details of the dongles and the results from sdptool. 
 
jaunty:~$ sdptool browse 00:22:A9:68:E2:2E
Browsing 00:22:A9:68:E2:2E ...
Service Name: Service Discovery Server
Service RecHandle: 0x10000
Service Class ID List:
  "SDP Server" (0x1000)
Protocol Descriptor List:
  "L2CAP" (0x0100)
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "SDP Server" (0x1000)
    Version: 0x0100

Service Name: OBEX Object Push
Service RecHandle: 0x10001
Service Class ID List:
  "OBEX Object Push" (0x1105)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 6
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "OBEX Object Push" (0x1105)
    Version: 0x0100

Service Name: OBEX File Transfer
Service RecHandle: 0x10002
Service Class ID List:
  "OBEX File Transfer" (0x1106)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 7
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "OBEX File Transfer" (0x1106)
    Version: 0x0100

Service Name: AV Audio Source
Service RecHandle: 0x10003
Service Class ID List:
  "Audio Source" (0x110a)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 25
  "AVDTP" (0x0019)
    uint16: 0x100
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Advanced Audio" (0x110d)
    Version: 0x0100

Service Name: AV Remote Control Target
Service RecHandle: 0x10004
Service Class ID List:
  "AV Remote Target" (0x110c)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 23
  "AVCTP" (0x0017)
    uint16: 0x100
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "AV Remote" (0x110e)
    Version: 0x0100

Service Name: AV Remote Control
Service RecHandle: 0x10005
Service Class ID List:
  "AV Remote" (0x110e)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 23
  "AVCTP" (0x0017)
    uint16: 0x100
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "AV Remote" (0x110e)
    Version: 0x0100

Service Name: Phonebook Access PSE
Service RecHandle: 0x10006
Service Class ID List:
  "Phonebook Access - PSE" (0x112f)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 12
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Phonebook Access" (0x1130)
    Version: 0x0100

Service Name: Voice Gateway
Service RecHandle: 0x10007
Service Class ID List:
  "Headset Audio Gateway" (0x1112)
  "Generic Audio" (0x1203)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 3
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Headset" (0x1108)
    Version: 0x0100

Service Name: Voice Gateway
Service RecHandle: 0x10008
Service Class ID List:
  "Handsfree Audio Gateway" (0x111f)
  "Generic Audio" (0x1203)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 4
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Handsfree" (0x111e)
    Version: 0x0105

[B]Service Name: BT DIAG
Service RecHandle: 0x10009
Service Class ID List:
  "Serial Port" (0x1101)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 16
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Serial Port" (0x1101)[/B]

Service Name: Bluetooth Modem
Service RecHandle: 0x1000a
Service Class ID List:
  "Dialup Networking" (0x1103)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 8
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Dialup Networking" (0x1103)
    Version: 0x0100

jaunty:~$ lsusb
Bus 001 Device 007: ID 4971:ce18  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 003 Device 008: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)**
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by 73ckn797 on 2009-08-03
I have not bothered with trying to connect to the phone since my last post. I keep saying I will but just do not really have the need to do it. 

I will get around to it later. I can always use the Windows XP on my laptop and it works fine from that.

---

### Post by ground-pilot on 2009-08-30
I bought and installed a new nano bluetooth usb2.0 adapter for $9 from Frye's. 

This did NOTHING to help the Jaunty BitPim issue...

I rolled back to verious versions of BitPim to no avail. 

FINALLY SOLVED:

 [ [http://www.ubuntugeek.com/blueman-bluetooth-manager-for-ubuntu.html](http://www.ubuntugeek.com/blueman-bluetooth-manager-for-ubuntu.html) ]

Follow the instructions on the lined page, then add the key for the blueman dev group, and finally install and configure BitPim accordingly.

     sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 951DC1E2

     sudo apt-get update

     sudo apt-get install blueman

Worked when I pointed BitPim 1.0.6 to /dev/rfcomm0  after blueman was installed. BlueZ that ships with Jaunty is a piece of junk at this point. I am now going to retest the Motorolla Roker HD Bluetooth for audio perf on Jaunty again. Yippe...

---

