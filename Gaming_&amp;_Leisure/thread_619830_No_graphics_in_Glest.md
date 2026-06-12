---
title: "No graphics in Glest"
date: 2007-11-21
forum: Gaming &amp; Leisure
---

### Post by threethirty on 2007-11-21
Hello all,

My girlfriend is trying to run Glest 2.0.0 and she has no graphics. She is running Feisty.  Below are the output of the game in terminal and lshw. any ideas? 

thanks in advance!

```
robin@Crane:/$ glest
Try R300_SPAN_DISABLE_LOCKING env var if this hangs.
*********************************WARN_ONCE*********************************
File r300_vertexprog.c function valid_dst line 333
Output 3 not used by fragment program
***************************************************************************
Couldn't process event: Error creating texture 3D
*********************************WARN_ONCE*********************************
File r300_render.c function r300Fallback line 393
Software fallback:ctx->RenderMode != GL_RENDER
***************************************************************************
robin@Crane:/$
```

```
robin@Crane:/$ lshw
WARNING: you should run this program as super-user.
crane
description: Computer
width: 32 bits
*-core
description: Motherboard
physical id: 0
*-memory
description: System memory
physical id: 0
size: 767MB
*-cpu
product: AMD Sempron(tm) 2200+
vendor: Advanced Micro Devices [AMD]
physical id: 1
bus info: cpu@0
version: 6.8.1
size: 1650MHz
width: 32 bits
capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up ts
*-cache:0
description: L1 cache
physical id: 0
size: 128KB
*-cache:1
description: L2 cache
physical id: 1
size: 256KB
*-pci
description: Host bridge
product: VT8378 [KM400/A] Chipset Host Bridge
vendor: VIA Technologies, Inc.
physical id: c0000000
bus info: pci@00:00.0
version: 00
width: 32 bits
clock: 66MHz
configuration: latency=8
resources: iomemory:c0000000-cfffffff
*-pci
description: PCI bridge
product: VT8237 PCI Bridge
vendor: VIA Technologies, Inc.
physical id: 1
bus info: pci@00:01.0
version: 00
width: 32 bits
clock: 66MHz
capabilities: pci normal_decode bus_master cap_list
*-display:0
description: VGA compatible controller
product: RV350 AS [Radeon 9550]
vendor: ATI Technologies Inc
physical id: 0
bus info: pci@01:00.0
version: 00
size: 128MB
width: 32 bits
clock: 66MHz
capabilities: vga bus_master cap_list
configuration: latency=32 mingnt=8
resources: iomemory:d0000000-d7ffffff ioport:9000-90ff iomemory:e0020000-e002ffff irq:20
*-display:1 UNCLAIMED
description: Display controller
product: RV350 AS [Radeon 9550] (Secondary)
vendor: ATI Technologies Inc
physical id: 0.1
bus info: pci@01:00.1
version: 00
size: 128MB
width: 32 bits
clock: 66MHz
capabilities: cap_list
configuration: latency=32 mingnt=8
resources: iomemory:d8000000-dfffffff iomemory:e0030000-e003ffff
*-communication UNCLAIMED
description: Communication controller
product: HCF 56k Data/Fax Modem
vendor: Conexant
physical id: 9
bus info: pci@00:09.0
version: 08
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: latency=32
resources: iomemory:e0100000-e010ffff ioport:a000-a007 irq:12
*-multimedia
description: Multimedia audio controller
product: SB Live! EMU10k1
vendor: Creative Labs
physical id: a
bus info: pci@00:0a.0
version: 08
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2
resources: ioport:a400-a41f irq:19
*-input
description: Input device controller
product: SB Live! Game Port
vendor: Creative Labs
physical id: a.1
bus info: pci@00:0a.1
version: 08
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: driver=Emu10k1_gameport latency=32
resources: ioport:a800-a807
*-usb:0
description: USB Controller
product: VT82xxxxx UHCI USB 1.1 Controller
vendor: VIA Technologies, Inc.
physical id: 10
bus info: pci@00:10.0
version: 80
width: 32 bits
clock: 33MHz
capabilities: uhci bus_master cap_list
configuration: driver=uhci_hcd latency=32
resources: ioport:ac00-ac1f irq:16
*-usbhost
product: UHCI Host Controller
vendor: Linux 2.6.20-16-generic uhci_hcd
physical id: 1
bus info: usb@1
logical name: usb1
version: 2.06
capabilities: usb-1.10
configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
*-usb
description: Mouse
product: USB-PS/2 Optical Mouse
vendor: Logitech
physical id: 2
bus info: usb@1:2
version: 20.00
capabilities: usb-2.00
configuration: driver=usbhid maxpower=98mA speed=1.5MB/s
*-usb:1
description: USB Controller
product: VT82xxxxx UHCI USB 1.1 Controller
vendor: VIA Technologies, Inc.
physical id: 10.1
bus info: pci@00:10.1
version: 80
width: 32 bits
clock: 33MHz
capabilities: uhci bus_master cap_list
configuration: driver=uhci_hcd latency=32
resources: ioport:b000-b01f irq:16
*-usbhost
product: UHCI Host Controller
vendor: Linux 2.6.20-16-generic uhci_hcd
physical id: 1
bus info: usb@2
logical name: usb2
version: 2.06
capabilities: usb-1.10
configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
*-usb:2
description: USB Controller
product: VT82xxxxx UHCI USB 1.1 Controller
vendor: VIA Technologies, Inc.
physical id: 10.2
bus info: pci@00:10.2
version: 80
width: 32 bits
clock: 33MHz
capabilities: uhci bus_master cap_list
configuration: driver=uhci_hcd latency=32
resources: ioport:b400-b41f irq:16
*-usbhost
product: UHCI Host Controller
vendor: Linux 2.6.20-16-generic uhci_hcd
physical id: 1
bus info: usb@3
logical name: usb3
version: 2.06
capabilities: usb-1.10
configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
*-usb:3
description: USB Controller
product: USB 2.0
vendor: VIA Technologies, Inc.
physical id: 10.3
bus info: pci@00:10.3
version: 82
width: 32 bits
clock: 33MHz
capabilities: ehci bus_master cap_list
configuration: driver=ehci_hcd latency=32
resources: iomemory:e0110000-e01100ff irq:16
*-usbhost
product: EHCI Host Controller
vendor: Linux 2.6.20-16-generic ehci_hcd
physical id: 1
bus info: usb@4
logical name: usb4
version: 2.06
capabilities: usb-2.00
configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
*-isa
description: ISA bridge
product: VT8235 ISA Bridge
vendor: VIA Technologies, Inc.
physical id: 11
bus info: pci@00:11.0
version: 00
width: 32 bits
clock: 33MHz
capabilities: isa bus_master cap_list
configuration: latency=0
*-ide
description: IDE interface
product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
vendor: VIA Technologies, Inc.
physical id: 11.1
bus info: pci@00:11.1
version: 06
width: 32 bits
clock: 33MHz
capabilities: ide bus_master cap_list
configuration: driver=VIA_IDE latency=32
resources: iomemory:1f0-1f7 iomemory:3f0-3ef iomemory:170-177 iomemory:370-36f ioport:b800-b80f irq:18
*-ide:0
description: IDE Channel 0
physical id: 0
bus info: ide@0
logical name: ide0
clock: 33MHz
*-disk
product: WDC WD800BB-00DKA0
vendor: Western Digital
physical id: 0
bus info: ide@0.0
logical name: /dev/hda
capacity: 74GB
*-ide:1
description: IDE Channel 1
physical id: 1
bus info: ide@1
logical name: ide1
clock: 33MHz
*-cdrom:0
product: LITE-ON COMBO SOHC-5232K
physical id: 0
bus info: ide@1.0
logical name: /dev/hdc
capabilities: packet
*-cdrom:1
product: MAD DOG MD-52XCDR
physical id: 1
bus info: ide@1.1
logical name: /dev/hdd
capabilities: packet
*-network
description: Ethernet interface
product: VT6102 [Rhine-II]
vendor: VIA Technologies, Inc.
physical id: 12
bus info: pci@00:12.0
logical name: eth0
version: 74
serial: 00:11:5b:98:6f:07
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=via-rhine driverversion=1.4.2 ip=192.168.1.104 latency=32 maxlatency=8 mingnt=3 multicast=yes
resources: ioport:c000-c0ff iomemory:e0111000-e01110ff irq:17
robin@Crane:/$ 
```

---

