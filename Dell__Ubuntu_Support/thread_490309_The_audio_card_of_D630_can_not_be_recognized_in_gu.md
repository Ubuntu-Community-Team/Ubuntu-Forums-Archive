---
title: "The audio card of D630 can not be recognized in gusty."
date: 2007-07-02
forum: Dell  Ubuntu Support
---

### Post by cnshzj007 on 2007-07-02
Some pictures show below may help you know detail to help me in a hurry.

---

### Post by cnshzj007 on 2007-07-02
The Chinese words in 1st pic says that "audio control can not find any equipment of audio.That may be the reason that gstreamer plugins are not installed correctly or audio card is not configured right."

---

### Post by cnshzj007 on 2007-07-02
bond007@ubuntu007:~$ sudo lshw
[sudo] password for bond007:
ubuntu007                 
    description: Portable Computer
    product: Latitude D630
    vendor: Dell Inc.
    serial: 1YRB52X
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=portable uuid=44454C4C-5900-1052-8042-B1C04F353258
  *-core
       description: Motherboard
       product: 0YK372
       vendor: Dell Inc.
       physical id: 0
       serial: .1YRB52X.CN129617642899.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A01 (05/18/2007)
          size: 64KB
          capacity: 1984KB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: Microprocessor
          size: 1801MHz
          capacity: 1801MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 32KB
             capacity: 32KB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 2MB
             capacity: 2MB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 1536MB
        *-bank:0
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             product: HYMP564S64CP6-Y5
             vendor: AD00000000000000
             physical id: 0
             serial: 00003057
             slot: DIMM_A
             size: 512MB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             vendor: 7F98000000000000
             physical id: 1
             serial: 671614E6
             slot: DIMM_B
             size: 1GB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: Mobile Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0
             description: VGA compatible controller
             product: Mobile Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.22-7-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: /dev/usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.22-7-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: /dev/usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.22-7-generic ehci_hcd
                physical id: 1
                bus info: usb@6
                logical name: /dev/usb6
                version: 2.06
                capabilities: usb-2.00
                configuration: maxpower=0mA slots=4 speed=480.0MB/s
        *-multimedia UNCLAIMED
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress cap_list
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Network controller
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=ipw3945 latency=0 module=ipw3945
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth0
                version: 02
                serial: 00:18:8b:da:c1:e8
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 duplex=full firmware=5755m-v3.29 ip=192.168.1.6 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.22-7-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: /dev/usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.22-7-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: /dev/usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: maxpower=0mA slots=2 speed=12.0MB/s
              *-usb UNCLAIMED
                   description: Generic USB device
                   product: USB Mouse
                   physical id: 1
                   bus info: usb@4:1
                   version: 2.30
                   capabilities: usb-1.00
                   configuration: maxpower=48mA speed=1.5MB/s
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.22-7-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: /dev/usb5
                version: 2.06
                capabilities: usb-1.10
                configuration: maxpower=0mA slots=2 speed=12.0MB/s
              *-usb UNCLAIMED
                   description: USB hub
                   physical id: 1
                   bus info: usb@5:1
                   version: 1.10
                   capabilities: usb-1.10
                   configuration: maxpower=2mA slots=4 speed=12.0MB/s
                 *-usb UNCLAIMED
                      description: Generic USB device
                      product: O2Micro CCID SC Reader
                      vendor: O2
                      physical id: 2
                      bus info: usb@5:1.2
                      version: 1.10
                      capabilities: usb-1.10
                      configuration: maxpower=0mA speed=12.0MB/s
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.22-7-generic ehci_hcd
                physical id: 1
                bus info: usb@7
                logical name: /dev/usb7
                version: 2.06
                capabilities: usb-2.00
                configuration: maxpower=0mA slots=6 speed=480.0MB/s
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-pcmcia
                description: CardBus bridge
                product: Cardbus bridge
                vendor: O2 Micro, Inc.
                physical id: 1
                bus info: pci@0000:03:01.0
                version: 21
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-firewire
                description: FireWire (IEEE 1394)
                product: Firewire (IEEE 1394)
                vendor: O2 Micro, Inc.
                physical id: 1.4
                bus info: pci@0000:03:01.4
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 module=ohci1394
        *-isa
             description: ISA bridge
             product: Mobile LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0 UNCLAIMED
             description: IDE interface
             product: Mobile IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: latency=0
        *-ide:1
             description: IDE interface
             product: Mobile SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: SCSI Disk
                product: Hitachi HTS72108
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: MC4O
                serial: MPCDN7Y4HU70VL
                size: 74GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Dell Utility partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 47MB
                   capabilities: primary
              *-volume:1
                   description: HPFS/NTFS partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 12GB
                   capabilities: primary
              *-volume:2
                   description: Linux filesystem partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 59GB
                   capabilities: primary bootable
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 2635MB
                   capacity: 2635MB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2635MB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-battery
       product: DELL DU15175
       vendor: Sanyo
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 52000mWh
       configuration: voltage=11.1V

---

### Post by cnshzj007 on 2007-07-02
[B][B][B][COLOR="RoyalBlue"]*-multimedia UNCLAIMED
description: Audio device
product: 82801H (ICH8 Family) HD Audio Controller
vendor: Intel Corporation
physical id: 1b
bus info: pci@0000:00:1b.0
version: 02
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress cap_list
configuration: latency=0[/COLOR][/B][/B][/B]

---

