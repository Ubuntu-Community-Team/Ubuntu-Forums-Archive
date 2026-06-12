---
title: "Generic USB Game Controller Dragonrise Inc."
date: 2015-11-13
forum: Gaming &amp; Leisure
---

### Post by vivichrist on 2015-11-13
[IMG]http://trademe.tmcdn.co.nz/photoserver/full/364042748.jpg[/IMG]
I bought a pair of the above. I know what you're thinking 'these are generic Chinese made cheap crap' and you would be right but I would still like to get them working properly.
And I have had some success in that they show up when I use jstest-gtk and the responces shown in that interface are a good sign that these work to some extent.
However, when I move the left stick to the left or right, the right stick also moves left and right respectively (up and down movement is unaffected). When I move the right stick up/down the left/right of the right stick are affected but not to exactly the same degree (the numbers marginally proportionately less relative to center.) All of this is with the Analog setting, otherwise the right stick maps to the x y a b or shape buttons. Also ABS_X, ABS_Y is the left stick... as per usual, but ABS_Z and ABS_RZ is the right stick, which is weird?

I'm looking for some way to fix this and I have scoured the net but I don't really know what phrase to search with. I have tried combinations of gamepad, game controller, dragonrise inc. etc.

```
  looking at device '/devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1.3/3-1.3:1.0/0003:0079:0006.0001/input/input14/event7':
    KERNEL=="event7"
    SUBSYSTEM=="input"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1.3/3-1.3:1.0/0003:0079:0006.0001/input/input14':
    KERNELS=="input14"
    SUBSYSTEMS=="input"
    DRIVERS==""
    ATTRS{name}=="DragonRise Inc.   Generic   USB  Joystick  "
    ATTRS{phys}=="usb-0000:00:1d.0-1.3/input0"
    ATTRS{properties}=="0"
    ATTRS{uniq}==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1.3/3-1.3:1.0/0003:0079:0006.0001':
    KERNELS=="0003:0079:0006.0001"
    SUBSYSTEMS=="hid"
    DRIVERS=="dragonrise"
    ATTRS{country}=="21"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1.3/3-1.3:1.0':
    KERNELS=="3-1.3:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="usbhid"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bInterfaceClass}=="03"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bInterfaceProtocol}=="00"
    ATTRS{bInterfaceSubClass}=="00"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{supports_autosuspend}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1.3':
    KERNELS=="3-1.3"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{authorized}=="1"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bMaxPacketSize0}=="8"
    ATTRS{bMaxPower}=="500mA"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bcdDevice}=="0107"
    ATTRS{bmAttributes}=="80"
    ATTRS{busnum}=="3"
    ATTRS{configuration}==""
    ATTRS{devnum}=="3"
    ATTRS{devpath}=="1.3"
    ATTRS{idProduct}=="0006"
    ATTRS{idVendor}=="0079"
    ATTRS{ltm_capable}=="no"
    ATTRS{manufacturer}=="DragonRise Inc.  "
    ATTRS{maxchild}=="0"
    ATTRS{product}=="Generic   USB  Joystick  "
    ATTRS{quirks}=="0x0"
    ATTRS{removable}=="removable"
    ATTRS{speed}=="1.5"
    ATTRS{urbnum}=="10190"
    ATTRS{version}==" 1.00"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb3/3-1':
    KERNELS=="3-1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{authorized}=="1"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{bMaxPower}=="0mA"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bcdDevice}=="0004"
    ATTRS{bmAttributes}=="e0"
    ATTRS{busnum}=="3"
    ATTRS{configuration}==""
    ATTRS{devnum}=="2"
    ATTRS{devpath}=="1"
    ATTRS{idProduct}=="8000"
    ATTRS{idVendor}=="8087"
    ATTRS{ltm_capable}=="no"
    ATTRS{maxchild}=="8"
    ATTRS{quirks}=="0x0"
    ATTRS{removable}=="fixed"
    ATTRS{speed}=="480"
    ATTRS{urbnum}=="34"
    ATTRS{version}==" 2.00"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb3':
    KERNELS=="usb3"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{authorized}=="1"
    ATTRS{authorized_default}=="1"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{bMaxPower}=="0mA"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bcdDevice}=="0402"
    ATTRS{bmAttributes}=="e0"
    ATTRS{busnum}=="3"
    ATTRS{configuration}==""
    ATTRS{devnum}=="1"
    ATTRS{devpath}=="0"
    ATTRS{idProduct}=="0002"
    ATTRS{idVendor}=="1d6b"
    ATTRS{ltm_capable}=="no"
    ATTRS{manufacturer}=="Linux 4.2.0-18-generic ehci_hcd"
    ATTRS{maxchild}=="2"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{quirks}=="0x0"
    ATTRS{removable}=="unknown"
    ATTRS{serial}=="0000:00:1d.0"
    ATTRS{speed}=="480"
    ATTRS{urbnum}=="24"
    ATTRS{version}==" 2.00"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0':
    KERNELS=="0000:00:1d.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci-pci"
    ATTRS{broken_parity_status}=="0"
    ATTRS{class}=="0x0c0320"
    ATTRS{companion}==""
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{d3cold_allowed}=="1"
    ATTRS{device}=="0x9c26"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{driver_override}=="(null)"
    ATTRS{enable}=="1"
    ATTRS{irq}=="23"
    ATTRS{local_cpulist}=="0-3"
    ATTRS{local_cpus}=="f"
    ATTRS{msi_bus}=="1"
    ATTRS{numa_node}=="-1"
    ATTRS{subsystem_device}=="0x201f"
    ATTRS{subsystem_vendor}=="0x1043"
    ATTRS{uframe_periodic_max}=="100"
    ATTRS{vendor}=="0x8086"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```

this is in Ubuntu 15.10

---

