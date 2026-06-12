---
title: "Determine USB 1 or 2 ?"
date: 2009-01-23
forum: General Help
---

### Post by zami on 2009-01-23
How can I tell if my machine has USB or USB2 ports?

-zami

---

### Post by mc4man on 2009-01-23
run this in terminal
```
lsusb
```

---

### Post by zami on 2009-01-23
Thanks!
lsusb gave me
```

laura@Silver:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

No idea what that means... also looked up the command lsusb for more info and then ran
lsusb -v
and got
```

laura@Silver:~$ lsusb -v

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

```
(Well, I got similar read outs six times as there are six ports.)

I'm sorry I just don't know what all this means.  Anyone care to translate for me?

-zami

---

### Post by fragos on 2009-01-23
Run "lspci". You'll find a number of line items for USB. As long as one of those lines says USB 2.0 that's what you got. Don't be concerned that all the other lines refer to USB 1.1.

---

### Post by zami on 2009-01-23
> **fragos said:**
> Run "lspci". You'll find a number of line items for USB. As long as one of those lines says USB 2.0 that's what you got. Don't be concerned that all the other lines refer to USB 1.1.
Fantastic, thank you!

-zami

---

### Post by Claudestephane on 2011-02-09
> **fragos said:**
> Run "lspci". You'll find a number of line items for USB. As long as one of those lines says USB 2.0 that's what you got. Don't be concerned that all the other lines refer to USB 1.1.

I ran your command & pasted output below: The only mention of USB2 is in the line I isolated w carriage returns. I have 4 USB ports on the computer, 2 in front & 2 in back. Controller #1, 2,3,4 are listed. As you can see the USB2 is onlt displayed after Controller #4. Does this mean only one port is USB ver 2, & other three ver 1 0r 1.1? I am trying to work out why Ubuntu 10.04 only sees the webcam component of my Logitech combined webcam/Mic device. The device works beautifully on my MAC. If I can get it to work on Linux box, will buy another webcam/mic. When I plug USB headset into another USB port simultaneously, Linux sees it well and I can adjust settings. It occurred to me that my motherboard might require video & audio streams to be fed through separate USB ports. No where could I find the issue addressed. Your wisdom welcome!


claude@claude-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 10)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 
EHCI Controller (rev 01)

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV44 [GeForce 7100 GS] (rev a1)
02:00.0 Ethernet controller: Atheros Communications Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)
04:01.0 Communication controller: 3Com Corp, Modem Division WinModem

---

### Post by fragos on 2011-02-09
The mixed reporting of USB 1 and 2 is what I've always gotten from every USB 2 mobo or USB 2 PCI card.

---

### Post by Claudestephane on 2011-02-09
> **fragos said:**
> The mixed reporting of USB 1 and 2 is what I've always gotten from every USB 2 mobo or USB 2 PCI card.

Do you interpret the following 


00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 
EHCI Controller (rev 01)

to mean each USB controller working each of 4 USB hardware ports, and only the #4 using the USB2 designation? 
But the basic question is can a combined webcam/mic plugged into one USB port be fully operational? When I plug logitech headset into one USB port and webcam/mic into another, both appear to function, but webcam/mic combo only allows webcam to be seen.

---

### Post by fragos on 2011-02-09
When you lsusb can you see the mic as a separate device? If not this may relate to the webcam driver. I don't have any good technical answers on USB. I only know what does and doesn't work for me. For example my webcam won't work if plugged into a USB hub but will plugged into any direct USB port.

---

