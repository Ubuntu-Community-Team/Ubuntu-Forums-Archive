---
title: "What sound driver do I pick?"
date: 2007-09-29
forum: Gaming &amp; Leisure
---

### Post by JESSU on 2007-09-29
I installed wow using wine but the sound is really chopped up.
Heres my specs

```
 description: Computer
    product: DIM4400
    vendor: Dell Computer Corporation
    version: TSMT
    serial: F1GY811
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal uuid=44454C4C-3100-1047-8059-C6C04F383131
  *-core
       description: Motherboard
       product: D845PT
       vendor: Intel Corporation
       physical id: 0
       version: AAA67829-304
       serial: MY00K9971246521F02JR
       slot: J1A1
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 1
          version: A06 (06/12/2002)
          size: 64KB
          capacity: 448KB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 1.80GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 15.1.2
          slot: J1E1
          size: 1800MHz
          capacity: 2GHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 6
             slot: None
             size: 8KB
             capacity: 8KB
             clock: 25MHz (40.0ns)
             capabilities: pipeline-burst synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: None
             size: 256KB
             capacity: 256KB
             capabilities: synchronous internal write-back unified
     *-memory
          description: System Memory
          physical id: 27
          slot: System board or motherboard
          size: 1GB
          capacity: 2GB
        *-bank:0
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             physical id: 0
             slot: J5G3
             size: 512MB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             physical id: 1
             slot: J5G1
             size: 512MB
             width: 64 bits
             clock: 266MHz (3.8ns)
     *-pci
          description: Host bridge
          product: 82845 845 (Brookdale) Chipset Host Bridge
          vendor: Intel Corporation
          physical id: f8000000
          bus info: pci@00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          resources: iomemory:f8000000-fbffffff
        *-pci:0
             description: PCI bridge
             product: 82845 845 (Brookdale) Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: NV34 [GeForce FX 5200]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a1
                size: 256MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
                resources: iomemory:fd000000-fdffffff iomemory:e0000000-efffffff irq:21
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-multimedia
                description: Multimedia audio controller
                product: SB Live! EMU10k1
                vendor: Creative Labs
                physical id: 9
                bus info: pci@02:09.0
                version: 07
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2
                resources: ioport:df80-df9f irq:18
           *-input
                description: Input device controller
                product: SB Live! Game Port
                vendor: Creative Labs
                physical id: 9.1
                bus info: pci@02:09.1
                version: 07
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=Emu10k1_gameport latency=32
                resources: ioport:dff0-dff7
           *-network
                description: Ethernet interface
                product: 21x4x DEC-Tulip compatible 10/100 Ethernet
                vendor: Davicom Semiconductor, Inc.
                physical id: b
                bus info: pci@02:0b.0
                logical name: eth0
                version: 31
                serial: 00:08:a1:0a:60:ea
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=dmfe driverversion=1.36.4 ip=192.168.1.104 latency=32 maxlatency=40 mingnt=20 multicast=yes
                resources: ioport:d800-d8ff iomemory:feaefc00-feaefcff irq:17
           *-usb:0
                description: USB Controller
                product: USB 1.1 Controller
                vendor: ALi Corporation
                physical id: c.1
                bus info: pci@02:0c.1
                version: 03
                width: 32 bits
                clock: 66MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci_hcd latency=32 maxlatency=80
                resources: iomemory:feafe000-feafefff irq:18
              *-usbhost
                   product: OHCI Host Controller
                   vendor: Linux 2.6.20-16-generic ohci_hcd
                   physical id: 1
                   bus info: usb@4
                   logical name: usb4
                   version: 2.06
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
           *-usb:1
                description: USB Controller
                product: USB 1.1 Controller
                vendor: ALi Corporation
                physical id: c
                bus info: pci@02:0c.0
                version: 03
                width: 32 bits
                clock: 66MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci_hcd latency=32 maxlatency=80
                resources: iomemory:feaed000-feaedfff irq:18
              *-usbhost
                   product: OHCI Host Controller
                   vendor: Linux 2.6.20-16-generic ohci_hcd
                   physical id: 1
                   bus info: usb@3
                   logical name: usb3
                   version: 2.06
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
           *-usb:2
                description: USB Controller
                product: USB 2.0 Controller
                vendor: ALi Corporation
                physical id: c.3
                bus info: pci@02:0c.3
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: ehci bus_master cap_list
                configuration: driver=ehci_hcd latency=32 maxlatency=80
                resources: iomemory:feaffc00-feaffcff irq:19
              *-usbhost
                   product: EHCI Host Controller
                   vendor: Linux 2.6.20-16-generic ehci_hcd
                   physical id: 1
                   bus info: usb@5
                   logical name: usb5
                   version: 2.06
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
                 *-usb
                      description: USB hub
                      physical id: 3
                      bus info: usb@5:3
                      version: 1.00
                      capabilities: usb-2.00
                      configuration: driver=hub maxpower=100mA slots=4 speed=480.0MB/s
           *-firewire
                description: FireWire (IEEE 1394)
                product: M5253 P1394 OHCI 1.1 Controller
                vendor: ALi Corporation
                physical id: c.4
                bus info: pci@02:0c.4
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=3
                resources: iomemory:feaef000-feaef7ff irq:20
        *-isa
             description: ISA bridge
             product: 82801BA ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801BA IDE U100
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated scsi-host
             configuration: driver=ata_piix latency=0
             resources: iomemory:1f0-1f7 iomemory:3f0-3ef iomemory:170-177 iomemory:370-36f ioport:ffa0-ffaf
           *-disk:0
                description: SCSI Disk
                product: WDC WD400BB-75CA
                vendor: ATA
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 16.0
                serial: WD-WMA8H2070912
                size: 37GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume
                   description: HPFS/NTFS partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 37GB
                   capabilities: primary bootable
           *-disk:1
                description: SCSI Disk
                product: IC35L120AVV207-1
                vendor: ATA
                physical id: 1
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: V24O
                serial: VNVD09G4H6TEKT
                size: 111GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   capacity: 110GB
                   capabilities: primary bootable
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.1.0,2
                   logical name: /dev/sdb2
                   size: 1474MB
                   capacity: 1474MB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 1474MB
                      capabilities: nofs
           *-cdrom:0
                description: DVD reader
                product: DVD-ROM LTD163
                vendor: LITEON
                physical id: 2
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: GDHA
                capabilities: removable audio dvd
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
           *-cdrom:1
                description: CD-R/CD-RW writer
                product: NR-7900A
                vendor: _NEC
                physical id: 3
                bus info: scsi@1:0.1.0
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 1.08
                serial: [_NEC    NR-7900A        1.0802011000
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/scd1
        *-usb:0
             description: USB Controller
             product: 82801BA/BAM USB (Hub #1)
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ef40-ef5f irq:16
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
                   product: USB Receiver
                   vendor: Logitech
                   physical id: 2
                   bus info: usb@1:2
                   version: 34.10
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=50mA speed=1.5MB/s
        *-serial UNCLAIMED
             description: SMBus
             product: 82801BA/BAM SMBus
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 05
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:efa0-efaf irq:10
        *-usb:1
             description: USB Controller
             product: 82801BA/BAM USB (Hub #2)
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@00:1f.4
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ef80-ef9f irq:17
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s

```

---

### Post by cogadh on 2007-09-29
WoW generally works best with OSS, but most other applications will get better performance with ALSA.

---

### Post by hikaricore on 2007-09-29
I've posted this like a dozen times now, but here goes again:

**Blizzard recently change the sound engine in WoW from HARDWARE accelerated to SOFTWARE emulated.**

What does this mean for you?  Well it means your audio card/chipset is no longer allowed to do it's job, and your cpu is doing all the work.
Many of us were using ALSA just perfectly until 2.2, now OSS is about the only way to go as the game is straight locking for many users /w ALSA.

---

### Post by JESSU on 2007-09-29
Thanks guys.
I will give OSS a try then. 
If this comes up a lot maybe it should be stickied

---

### Post by hikaricore on 2007-09-29
No point in that.  I've seen about 4-7 new threads about WoW per day since 2.2.

The posters would just ignore the stickies and make a new thread.

---

