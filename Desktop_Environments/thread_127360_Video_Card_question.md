---
title: "Video Card question"
date: 2006-02-08
forum: Desktop Environments
---

### Post by rado_london on 2006-02-08
Hi all
I am one very happy Linux user. I have HP Pavilion DV4145EA laptop, which by the way runs perfectly under Linux. But I have a little problem. How can I find what is my graphics card. Also I would like to find more aditional info for it ie how many MB etc.

Thank you in advance!!!

---

### Post by dcstar on 2006-02-09
[QUOTE=rado_london]Hi all
I am one very happy Linux user. I have HP Pavilion DV4145EA laptop, which by the way runs perfectly under Linux. But I have a little problem. How can I find what is my graphics card. Also I would like to find more aditional info for it ie how many MB etc.

Thank you in advance!!![/QUOTE]
lshw

---

### Post by nanotube on 2006-02-09
or, if you are a fan of the GUI, go to System > Administration > Device Manager
and look around. :)

---

### Post by rado_london on 2006-02-09
Thanks guys for the quick responce.
I tried lshw, but I am confused.
This is the output of lshw:
```
rado@linux:~$ sudo lshw
Password:
linux
    description: Notebook
    product: Pavilion dv4000 (EF176EA#ABU)
    vendor: Hewlett-Packard
    serial: 2CE53308SP
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: boot=normal chassis=notebook uuid=8D926AA0-10C5-11DA-B4C6-BBBDDA4C5EB1
  *-core
       description: Motherboard
       product: 09BC
       vendor: Hewlett-Packard
       physical id: 0
       version: 35.30
     *-firmware
          description: BIOS
          vendor: Phoenix
          physical id: 0
          version: F.16 (07/27/2005)
          size: 104KB
          capacity: 448KB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1.73GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.13.8
          slot: U1
          size: 1733MHz
          capacity: 1733MHz
          width: 32 bits
          clock: 533MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx est tm2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 32KB
             capacity: 32KB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 2MB
             capacity: 2MB
             capabilities: burst internal write-back unified
     *-memory
          description: System Memory
          physical id: f
          slot: System board or motherboard
          size: 512MB
          capacity: 3GB
        *-bank:0
             description: DIMM DDR Synchronous
             physical id: 0
             slot: M1
             size: 256MB
             width: 64 bits
        *-bank:1
             description: DIMM DDR Synchronous
             physical id: 1
             slot: M2
             size: 256MB
             width: 64 bits
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
        *-display:0
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             logical name: /dev/fb0
             version: 04
             size: 256MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list fb
             configuration: depth=32 frequency=75.69Hz mode=1024x768 visual=truecolor xres=1024 yres=768
             resources: iomemory:b0080000-b00fffff ioport:1800-1807 iomemory:c0000000-cfffffff iomemory:b0000000-b003ffff irq:16
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@00:02.1
             version: 04
             size: 512KB
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             resources: iomemory:20000000-2007ffff
        *-pci:0
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@00:1c.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1820-183f irq:23
           *-usbhost
                product: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
                vendor: Linux 2.6.12-10-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mouse
                   product: Microsoft Notebook/Mobile Optical Mouse 2.0
                   vendor: Microsoft
                   physical id: 1
                   bus info: usb@1:1
                   version: 2.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1840-185f irq:19
           *-usbhost
                product: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
                vendor: Linux 2.6.12-10-386 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1860-187f irq:18
           *-usbhost
                product: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
                vendor: Linux 2.6.12-10-386 uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@00:1d.3
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1880-189f irq:16
           *-usbhost
                product: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
                vendor: Linux 2.6.12-10-386 uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:b0040000-b00403ff irq:23
           *-usbhost
                product: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
                vendor: Linux 2.6.12-10-386 ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: d4
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-network:0
                description: Wireless interface
                product: PRO/Wireless 2200BG
                vendor: Intel Corporation
                physical id: 5
                bus info: pci@06:05.0
                logical name: eth0
                version: 05
                serial: 00:12:f0:dc:33:66
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.0.6 firmware=ABG:9.0.1.5 (Oct 15 2004) ip=192.168.0.2 link=yes multicast=yes wireless=IEEE 802.11g
                resources: iomemory:b0106000-b0106fff irq:20
           *-pcmcia
                description: CardBus bridge
                product: Texas Instruments PCIxx21/x515 Cardbus Controller
                vendor: Texas Instruments
                physical id: 6
                bus info: pci@06:06.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:b0107000-b0107fff irq:22
           *-firewire
                description: FireWire (IEEE 1394)
                product: Texas Instruments OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 6.2
                bus info: pci@06:06.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394
                resources: iomemory:b0108000-b01087ff iomemory:b0100000-b0103fff irq:21
           *-storage UNCLAIMED
                description: Unknown mass storage controller
                product: Texas Instruments PCIxx21 Integrated FlashMedia Controller
                vendor: Texas Instruments
                physical id: 6.3
                bus info: pci@06:06.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage bus_master cap_list
                resources: iomemory:b0104000-b0105fff irq:10
           *-system UNCLAIMED
                description: Generic system peripheral
                product: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller
                vendor: Texas Instruments
                physical id: 6.4
                bus info: pci@06:06.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                resources: iomemory:b0109000-b01090ff iomemory:b0108c00-b0108cff iomemory:b0108800-b01088ff irq:10
           *-network:1 DISABLED
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 7
                bus info: pci@06:07.0
                logical name: eth1
                version: 10
                serial: 00:0a:e4:d6:a6:9d
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
                configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=half link=no multicast=yes port=MII speed=10MB/s
                resources: ioport:3000-30ff iomemory:b0109400-b01094ff irq:20
        *-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@00:1e.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH
             resources: ioport:1c00-1cff ioport:18c0-18ff iomemory:b0040800-b00409ff iomemory:b0040400-b00404ff irq:17
        *-communication UNCLAIMED
             description: Modem
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller             vendor: Intel Corporation
             physical id: 1e.3
             bus info: pci@00:1e.3
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: generic cap_list
             resources: ioport:2400-24ff ioport:2000-207f irq:20
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801FBM (ICH6M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:1810-181f irq:18
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: FUJITSU MHT2080AT PL
                   vendor: Fujitsu
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 0022
                   serial: NN4FT571C9D7
                   size: 74GB
                   capacity: 74GB
                   capabilities: ata dma lba iordy smart security pm apm
                   configuration: apm=off mode=udma5 smart=on
              *-cdrom
                   description: DVD writer
                   product: TSSTcorpCD/DVDW TS-L532R
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: HA04
                   serial: 554B600455
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw dvd dvd-r
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 04
             width: 32 bits
             clock: 33MHz
             resources: ioport:18a0-18bf irq:10
```


Now can someone tell me how many MB is my graphics card.

Thanks again:D :D :D :D :D

---

### Post by Ramses de Norre on 2006-02-09
```
*-display:0
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             logical name: /dev/fb0
             version: 04
             size: 256MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list fb
             configuration: depth=32 frequency=75.69Hz mode=1024x768 visual=truecolor xres=1024 yres=768
             resources: iomemory:b0080000-b00fffff ioport:1800-1807 iomemory:c0000000-cfffffff iomemory:b0000000-b003ffff irq:16
```
I think that's the right section, so 256MB

---

### Post by rado_london on 2006-02-09
Haha But when I bought my laptop they said to me that it is shared so  it would not be that good, but 256 MB seems a bit much isnt it? Is that a mistake or misunderstanding?

Thanks for the responce again

---

### Post by Ramses de Norre on 2006-02-09
I don't know whether the 256MB is the shared memory or memory of the graph card itself, I just compared your output to mine..
It's showing the non-shared output in my lshw-output.
But maybe there is no diferent in that output when you're using shared memory..

---

### Post by rado_london on 2006-02-09
Thanks.
Does the 256 MB means that II can Play Doom 3 with no issues?

---

