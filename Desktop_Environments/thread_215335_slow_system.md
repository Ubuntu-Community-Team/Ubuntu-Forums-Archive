---
title: "slow system"
date: 2006-07-13
forum: Desktop Environments
---

### Post by davebradford on 2006-07-13
hi there i'm currantly running ubuntu dapper drake on my system with a laptop, it's around 3 years old and i have noticed that it's a little slow at responding, not loads but enough for it to be anonoying! anybody got any little ideas on how i can combat this maybe with little tweeks or script editing?

thanks..

---

### Post by T700 on 2006-07-13
A good first step would be to post the specs for your laptop.  You can go to a terminal session and type:

```
sudo lshw
```

and post the results.  That will give people a good starting point to make suggestions.

Paul

---

### Post by davebradford on 2006-07-22
my specs r as follows:

Intel Celeron 1.0 Ghz
256 SD-RAM
S3 Gfx Card - 32MB Shared Memory.

---

### Post by davebradford on 2006-07-22
Ok sorry i've done that commend for the system specification and this is the result. Thanks for your help.

laptop
    description: Computer
    product: Aspire 1200 series
    vendor: Acer
    version: N/A
    serial: LXA010515522416986EB00
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: administrator_password=enabled boot=oem-specific frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=00000000-0000-0000-0000-0090962A19FD
  *-core
       description: Motherboard
       product: 8606-686B
       vendor: CY23
       physical id: 0
       version: None
       serial: None
     *-firmware
          description: BIOS
          vendor: Phoenix
          physical id: 0
          version: V2.00 (06/25/2002)
          size: 86KB
          capacity: 192KB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd usb smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Celeron(TM) CPU                1300MHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.11.1
          slot: Socket 370
          size: 1300MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: L1 Cache
             size: 32KB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: a
             slot: L2 Cache
             size: 256KB
             capacity: 512KB
             capabilities: burst external write-through
     *-memory
          description: System Memory
          physical id: 24
          slot: System board or motherboard
          size: 256MB
          capacity: 384MB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: M1
             size: 128MB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: M2
             size: 128MB
             width: 64 bits
        *-bank:2
             description: DIMM DRAM Synchronous [empty]
             physical id: 2
             slot: M3
     *-pci
          description: Host bridge
          product: VT8605 [ProSavage PM133]
          vendor: VIA Technologies, Inc.
          physical id: ec000000
          bus info: pci@00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          resources: iomemory:ec000000-efffffff
        *-pci
             description: PCI bridge
             product: VT8605 [PM133 AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: 86C380 [ProSavageDDR K4M266]
                vendor: S3 Inc.
                physical id: 0
                bus info: pci@01:00.0
                version: 02
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:e8100000-e817ffff iomemory:f0000000-f7ffffff irq:10
        *-pcmcia:0
             description: CardBus bridge
             product: OZ6933/711E1 CardBus/SmartCardBus Controller
             vendor: O2 Micro, Inc.
             physical id: 4
             bus info: pci@00:04.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:18020000-18020fff irq:10
           *-network
                description: Card
                product: ISL37300P
                vendor: NETGEAR MA401RA Wireless PC
                physical id: 0
                version: Eval-RevA
                slot: Socket 0
                resources: irq:3
        *-pcmcia:1
             description: CardBus bridge
             product: OZ6933/711E1 CardBus/SmartCardBus Controller
             vendor: O2 Micro, Inc.
             physical id: 4.1
             bus info: pci@00:04.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:18021000-18021fff irq:11
        *-isa:0
             description: ISA bridge
             product: VT82C686 [Apollo Super South]
             vendor: VIA Technologies, Inc.
             physical id: 7
             bus info: pci@00:07.0
             version: 42
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=parport_pc
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 7.1
             bus info: pci@00:07.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=VIA_IDE
             resources: ioport:1000-100f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: IC25N020ATCS04-0
                   vendor: Hitachi
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: CA2OA71A
                   serial: CSH201D2D91HDB
                   size: 18GB
                   capacity: 18GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma5 smart=on
                 *-volume:0
                      description: Linux swap / Solaris partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 956MB
                      capabilities: primary nofs
                 *-volume:1
                      description: Linux filesystem partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 17GB
                      capabilities: primary
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD reader
                   product: TOSHIBA DVD-ROM SD-R2102
                   vendor: Toshiba
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 1015
                   serial: 424A400756
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-usb
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.2
             bus info: pci@00:07.2
             version: 1a
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:1020-103f irq:11
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-26-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mouse
                   product: Microsoft 3-Button Mouse with IntelliEye(TM)
                   vendor: Microsoft
                   physical id: 1
                   bus info: usb@1:1
                   version: 3.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-isa:1 UNCLAIMED
             description: ISA bridge
             product: VT82C686 [Apollo Super ACPI]
             vendor: VIA Technologies, Inc.
             physical id: 7.4
             bus info: pci@00:07.4
             version: 40
             width: 32 bits
             clock: 33MHz
             capabilities: isa cap_list
             resources: irq:9
        *-multimedia
             description: Multimedia audio controller
             product: VT82C686 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.5
             bus info: pci@00:07.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=VIA 82xx Audio
             resources: ioport:1400-14ff ioport:1014-1017 ioport:1010-1013 irq:5
        *-firewire
             description: FireWire (IEEE 1394)
             product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
             vendor: Texas Instruments
             physical id: d
             bus info: pci@00:0d.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci1394
             resources: iomemory:e8004000-e80047ff iomemory:e8000000-e8003fff irq:5
        *-communication UNCLAIMED
             description: Communication controller
             product: LT WinModem
             vendor: Agere Systems
             physical id: 10
             bus info: pci@00:10.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             resources: iomemory:e8004800-e80048ff ioport:1018-101f ioport:1800-18ff irq:11
        *-network
             description: Ethernet interface
             product: EN-1216 Ethernet Adapter
             vendor: Accton Technology Corporation
             physical id: 11
             bus info: pci@00:11.0
             logical name: eth0
             version: 11
             serial: 00:90:96:2a:19:fd
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=tulip driverversion=1.1.13 multicast=yes
             resources: ioport:1c00-1cff iomemory:e8004c00-e8004fff irq:11
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:09:5b:55:1c:b4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15rc3 firmware=Intersil 1.3.6 ip=192.168.170.40 link=yes multicast=yes wireless=IEEE 802.11b

---

### Post by taurus on 2006-07-22
With 256MB of RAM for Gnome, it will be a little slow so use Xfce4 or even fluxbox if you want it to speed up a little!!!

---

### Post by cptnapalm on 2006-07-22
Gnome has really bloated... years ago, I ran Gnome fine on a K6-233 with 128 MB of RAM...

---

### Post by davebradford on 2006-07-24
thanks for the advice might try using fluxbox.. it seems quite good. is there nothing to do to 'un-bloat' gnome..?

---

### Post by davebradford on 2006-07-25
bump!

---

### Post by Tux+ on 2006-08-05
If something is bloated then you can't really do much to "un-bloat" it unless you go into the code and start stripping it out. I say try XFCE because it's similar to KDE in some ways

---

### Post by davebradford on 2006-08-08
the laptop is not running mega slow but if i can  get it to go faster i'll try all i can! i've been using bum to try and save time booting up. i'm not really a big KDE so i dont think XFCE is for me... fluxbox is good but too much effort to get setup and access things!

---

