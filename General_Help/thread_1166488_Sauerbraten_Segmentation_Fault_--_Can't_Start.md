---
title: "Sauerbraten Segmentation Fault -- Can't Start"
date: 2009-05-21
forum: General Help
---

### Post by ALIENDUDE5300 on 2009-05-21
Hi, after installing Sauerbraten from the repositories, I get the following output after running it in the terminal:
```
Using home directory: /home/owner/.sauerbraten
init: sdl
init: enet
init: video: mode
init: video: misc
init: gl
Renderer: ATI Radeon HD 4800 Series (ATI Technologies Inc.)
Driver: 2.1.8575
Rendering using the OpenGL 1.5 GLSL shader path.
init: console
init: gl: effects
init: world
Segmentation fault

```
My graphics card is an ATI HD 4850, I have 3 Gigs of DDR3 Ram, and I'm on an Intel Core i7 CPU @ 2.67Ghz. There's almost no way this is a hardware problem, and I think all the required dependencies are installed. I'm currently using the proprietary ATI drivers (mesa is terrible for almost anything gaming related). Any help would be appreciated, I'm clueless as to what is wrong.
Here is the output of lshw (as root):
```

    description: Desktop Computer
    product: FX6800-01e
    vendor: Gateway
    serial: PTG410X00184907C4F2700
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: administrator_password=disabled boot=normal chassis=desktop cpus=4 frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled uuid=0022683A-EA60-2008-1204-095953000000
  *-core
       description: Motherboard
       product: TBGM01
       vendor: Gateway
       physical id: 0
       serial: U00B084900869
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: AMI
          physical id: 0
          version: R01-A1 (10/29/2008)
          size: 128KiB
          capacity: 960KiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.10.4
          serial: 0001-06A4-0000-0000-0000-0000
          slot: CPU 1
          size: 2667MHz
          capacity: 2667MHz
          width: 64 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts xtopology pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 lahf_lm ida tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: internal write-back unified
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 8MiB
             capacity: 8MiB
             capabilities: internal write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 0.3
             width: 64 bits
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 0.4
             width: 64 bits
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 0.5
             width: 64 bits
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 0.6
             width: 64 bits
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 0.7
             width: 64 bits
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 0.8
             width: 64 bits
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 0.9
             width: 64 bits
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 0.a
             width: 64 bits
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 0.b
             width: 64 bits
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 0.c
             width: 64 bits
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 0.d
             width: 64 bits
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 0.e
             width: 64 bits
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 0.f
             width: 64 bits
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 0.10
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 1d
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM 1067 MHz (0.9 ns)
             product: M378B2873DZ1-CF8
             vendor: Samsung
             physical id: 0
             serial: A1854A42
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
        *-bank:1
             description: DIMM [empty]
             vendor: None
             physical id: 1
             serial: 00000000
             slot: DIMM1
             width: 64 bits
        *-bank:2
             description: DIMM 1067 MHz (0.9 ns)
             product: M378B2873DZ1-CF8
             vendor: Samsung
             physical id: 2
             serial: 7D854A42
             slot: DIMM2
             size: 1GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
        *-bank:3
             description: DIMM [empty]
             vendor: None
             physical id: 3
             serial: 00000000
             slot: DIMM3
             width: 64 bits
        *-bank:4
             description: DIMM 1067 MHz (0.9 ns)
             product: M378B2873DZ1-CF8
             vendor: Samsung
             physical id: 4
             serial: 90854A42
             slot: DIMM4
             size: 1GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
        *-bank:5
             description: DIMM [empty]
             vendor: None
             physical id: 5
             serial: 00000000
             slot: DIMM5
             width: 64 bits
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.10.4
          serial: 0001-06A4-0000-0000-0000-0000
          size: 2667MHz
          capacity: 2667MHz
          capabilities: vmx ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 0.3
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 0.4
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 0.5
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 0.6
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 0.7
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 0.8
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 0.9
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 0.a
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 0.b
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 0.c
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 0.d
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 0.e
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 0.f
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 0.10
             capabilities: logical
     *-cpu:2
          physical id: 2
          bus info: cpu@2
          version: 6.10.4
          serial: 0001-06A4-0000-0000-0000-0000
          size: 2667MHz
          capacity: 2667MHz
          capabilities: vmx ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 0.3
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 0.4
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 0.5
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 0.6
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 0.7
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 0.8
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 0.9
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 0.a
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 0.b
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 0.c
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 0.d
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 0.e
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 0.f
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 0.10
             capabilities: logical
     *-cpu:3
          physical id: 3
          bus info: cpu@3
          version: 6.10.4
          serial: 0001-06A4-0000-0000-0000-0000
          size: 2667MHz
          capacity: 2667MHz
          capabilities: vmx ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 0.3
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 0.4
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 0.5
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 0.6
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 0.7
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 0.8
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 0.9
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 0.a
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 0.b
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 0.c
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 0.d
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 0.e
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 0.f
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 0.10
             capabilities: logical
     *-pci
          description: Host bridge
          product: X58 I/O Hub to ESI Port
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 12
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: X58 I/O Hub PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-storage
                description: SATA controller
                product: JMicron 20360/20363 AHCI Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress bus_master cap_list
                configuration: driver=ahci latency=0 module=ahci
           *-ide
                description: IDE interface
                product: JMicron 20360/20363 AHCI Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0.1
                bus info: pci@0000:05:00.1
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm bus_master cap_list
                configuration: driver=pata_jmicron latency=0
        *-pci:1
             description: PCI bridge
             product: X58 I/O Hub PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: RV770 [Radeon HD 4850]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=fglrx_pci latency=0 module=fglrx
           *-multimedia
                description: Audio device
                product: HD48x0 audio
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:04:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:2
             description: PCI bridge
             product: X58 I/O Hub PCI Express Root Port 7
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-system:0 UNCLAIMED
             description: PIC
             product: X58 Physical and Link Layer Registers Port 0
             vendor: Intel Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
        *-system:1 UNCLAIMED
             description: PIC
             product: X58 Routing and Protocol Layer Registers Port 0
             vendor: Intel Corporation
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 12
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-system:2 UNCLAIMED
             description: PIC
             product: X58 I/O Hub I/OxAPIC Interrupt Controller
             vendor: Intel Corporation
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-system:3 UNCLAIMED
             description: PIC
             product: X58 I/O Hub System Management Registers
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-system:4 UNCLAIMED
             description: PIC
             product: X58 I/O Hub GPIO and Scratch Pad Registers
             vendor: Intel Corporation
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-system:5 UNCLAIMED
             description: PIC
             product: X58 I/O Hub Control Status and RAS Registers
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-system:6 UNCLAIMED
             description: PIC
             product: X58 I/O Hub Throttle Registers
             vendor: Intel Corporation
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 12
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-network
             description: Ethernet interface
             product: 82567LF-2 Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 00
             serial: 00:22:68:3a:ea:60
             size: 100MB/s
             capacity: 1GB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 duplex=full firmware=1.8-5 ip=192.168.1.6 latency=0 link=yes module=e1000e multicast=yes port=twisted pair speed=100MB/s
        *-usb:0
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801JI (ICH10 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801JI (ICH10 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:3
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-communication UNCLAIMED
                description: Communication controller
                product: Agere Systems
                vendor: Agere Systems
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
        *-usb:4
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:7
             description: USB Controller
             product: 82801JI (ICH10 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 90
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306 Fire II IEEE 1394 OHCI Link Layer Controller
                vendor: VIA Technologies, Inc.
                physical id: 6
                bus info: pci@0000:01:06.0
                version: c0
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=32 module=ohci1394
        *-isa
             description: ISA bridge
             product: 82801JIR (ICH10R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 82801JI (ICH10 Family) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi3
             logical name: scsi5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0 module=ahci
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GH15F
                vendor: HL-DT-ST
                physical id: 0
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: EG00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
           *-disk
                description: ATA Disk
                product: ST3750630AS
                vendor: Seagate
                physical id: 1
                bus info: scsi@5:0.0.0
                logical name: /dev/sda
                version: SD46
                serial: 9QK1XF6G
                size: 698GiB (750GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=b165686d
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@5:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: dc4c-e6ea
                   size: 10001MiB
                   capacity: 10001MiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2008-11-11 18:00:31 filesystem=ntfs label=PQSERVICE state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@5:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /media/OS
                   version: 3.1
                   serial: b47fc590-e176-7a4a-9b62-10ac5bd7783f
                   size: 372GiB
                   capacity: 372GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2008-11-11 19:12:32 filesystem=ntfs label=OS modified_by_chkdsk=true mount.fstype=fuseblk mount.options=rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 mounted_on_nt4=true resize_log_file=true state=mounted upgrade_on_mount=true
              *-volume:2
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@5:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /
                   version: 1.0
                   serial: 49606533-72e0-4758-b017-d56134875067
                   size: 316GiB
                   capacity: 316GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2009-05-20 21:52:54 filesystem=ext4 modified=2009-05-21 15:02:54 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2009-05-21 15:02:54 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 82801JI (ICH10 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 00
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
     *-scsi
          physical id: 5
          bus info: usb@1:3
          logical name: scsi10
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@10:0.0.0
             logical name: /dev/sdb
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: aa:61:30:77:ca:73
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

---

### Post by whitethorn on 2009-05-21
I don't really know what's the problem, but why don't you grab the new version of Sauerbraten?  @ [www.sauerbraten.org](www.sauerbraten.org)  .  All you gotta do is unpack it to something like ~/games/.  To start the game go into the folder and run.  I think I needed to install some sort of library, but I don't remember anymore.

```

 ./sauerbraten_unix

```

I got the old version of sauerbraten to play by using this webpage  

[www.playdeb.net](www.playdeb.net)

I just clicked on the install link above sauerbraten, it downloaded the prog, and installed it.

---

