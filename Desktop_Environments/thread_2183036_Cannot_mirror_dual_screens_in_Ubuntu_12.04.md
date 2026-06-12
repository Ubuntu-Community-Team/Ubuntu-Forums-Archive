---
title: "Cannot mirror dual screens in Ubuntu 12.04"
date: 2013-10-23
forum: Desktop Environments
---

### Post by Lars Noodén on 2013-10-23
I've got a laptop with an external screen which works fine when the screens are laid out in side-by-side mode.  What do I need to set up to get mirroring?  Currently that option is greyed out in System Settings -> Displays

---

### Post by Lars Noodén on 2013-10-24
It doesn't look like attachments are working.  Here is the output from lshw, if that helps.  The machine does have to stay with 12.04.x  Moving to 13.10 is not an option.   It's got an NVIDIA G98M [Quadro NVS 160M]



```

   id:
                  computer
   description:   Portable Computer
   product:       Latitude E6500 ()
   vendor:        Winbond Electronics
   serial:        [REMOVED]
   width:         64 bits
   capabilities:  smbios-2.4 dmi-2.4 vsyscall32
   configuration:
                  boot    = normal
                  chassis = portable
                  uuid    = [REMOVED]

   id:
                core
   description: Motherboard
   product:     0X564R
   vendor:      Winbond Electronics
   physical id:
                0
   serial:      [REMOVED]
   id:
   firmware
   description: BIOS
   vendor: Winbond Electronics
   physical id:
   0
   version: A19
   date: 12/21/2009
   size: 64KiB
   capacity: 1664KiB
   capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect
   int13floppy720 int5printscreen int9keyboard int14serial int17printer
   int10video acpi usb agp smartbattery biosbootspecification netboot
   id:
   cpu
   description: CPU
   product: Intel(R) Core(TM)2 Duo CPU P8600 @ 2.40GHz
   vendor: Intel Corp.
   physical id:
   400
   bus info:
   cpu@0
   slot: Microprocessor
   size: 800MHz
   capacity: 800MHz
   width: 64 bits
   clock: 266MHz
   capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce
   cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse
   sse2 ss ht tm pbe syscall nx constant_tsc arch_perfmon pebs bts
   rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2
   ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm ida dtherm tpr_shadow vnmi
   flexpriority cpufreq
   configuration:
   cores        = 2
   enabledcores = 2
   threads      = 2
   id:
                 cache:0
   description:  L1 cache
   physical id:
                 700
   size:         128KiB
   capacity:     128KiB
   capabilities: internal write-back data
   id:
                 cache:1
   description:  L2 cache
   physical id:
                 701
   size:         3MiB
   capacity:     3MiB
   clock:        66MHz (15.0ns)
   capabilities: pipeline-burst internal varies unified
   id:
                memory
   description: System Memory
   physical id:
                1000
   slot:        System board or motherboard
   size:        4GiB
   id:
                bank:0
   description: DIMM DDR2 Synchronous 800 MHz (1,2 ns)
   product:     HYMP125S64CP8-S6
   vendor:      Hynix Semiconductor (Hyundai Electronics)
   physical id:
                0
   serial:      [REMOVED]
   slot:        DIMM_A
   size:        2GiB
   width:       64 bits
   clock:       800MHz (1.2ns)
   id:
                bank:1
   description: DIMM DDR2 Synchronous 800 MHz (1,2 ns)
   product:     HYMP125S64CP8-S6
   vendor:      Hynix Semiconductor (Hyundai Electronics)
   physical id:
                1
   serial:      [REMOVED]
   slot:        DIMM_B
   size:        2GiB
   width:       64 bits
   clock:       800MHz (1.2ns)
   id:
                pci
   description: Host bridge
   product:     Mobile 4 Series Chipset Memory Controller Hub
   vendor:      Intel Corporation
   physical id:
                100
   bus info:
                pci@0000:00:00.0
   version:     07
   width:       32 bits
   clock:       33MHz
   id:
                  pci:0
   description:   PCI bridge
   product:       Mobile 4 Series Chipset PCI Express Graphics Port
   vendor:        Intel Corporation
   physical id:
                  1
   bus info:
                  pci@0000:00:01.0
   version:       07
   width:         32 bits
   clock:         33MHz
   capabilities:  pci pm msi pciexpress normal_decode bus_master cap_list
   configuration:
                  driver = pcieport
   resources:
                  irq    : 40
                  ioport : d000(size=4096)
                  memory : f2000000-f6efffff
                  ioport : e0000000(size=268435456)
   id:
                  display
   description:   VGA compatible controller
   product:       G98M [Quadro NVS 160M]
   vendor:        NVIDIA Corporation
   physical id:
                  0
   bus info:
                  pci@0000:01:00.0
   version:       a1
   width:         64 bits
   clock:         33MHz
   capabilities:  pm msi pciexpress vga_controller bus_master cap_list rom
   configuration:
                  driver  = nvidia
                  latency = 0
   resources:
                  irq    : 16
                  memory : f5000000-f5ffffff
                  memory : e0000000-efffffff
                  memory : f2000000-f3ffffff
                  ioport : df00(size=128)
                  memory : f4000000-f401ffff
   id:
                  network
   description:   Ethernet interface
   product:       82567LM Gigabit Network Connection
   vendor:        Intel Corporation
   physical id:
                  19
   bus info:
                  pci@0000:00:19.0
   logical name:
                  eth0
   version:       03
   serial:        [REMOVED]
   size:          100Mbit/s
   capacity:      1Gbit/s
   width:         32 bits
   clock:         33MHz
   capabilities:  pm msi bus_master cap_list ethernet physical tp 10bt
                  10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
   configuration:
                  autonegotiation = on
                  broadcast       = yes
                  driver          = e1000e
                  driverversion   = 1.5.1-k
                  duplex          = full
                  firmware        = 1.7-7
                  ip              = [REMOVED]
                  latency         = 0
                  link            = yes
                  multicast       = yes
                  port            = twisted pair
                  speed           = 100Mbit/s
   resources:
                  irq    : 46
                  memory : f6fe0000-f6ffffff
                  memory : f6fdb000-f6fdbfff
                  ioport : efe0(size=32)
   id:
                  usb:0
   description:   USB controller
   product:       82801I (ICH9 Family) USB UHCI Controller #4
   vendor:        Intel Corporation
   physical id:
                  1a
   bus info:
                  pci@0000:00:1a.0
   version:       03
   width:         32 bits
   clock:         33MHz
   capabilities:  uhci bus_master cap_list
   configuration:
                  driver  = uhci_hcd
                  latency = 0
   resources:
                  irq    : 20
                  ioport : 6f60(size=32)
   id:
                  usb:1
   description:   USB controller
   product:       82801I (ICH9 Family) USB UHCI Controller #5
   vendor:        Intel Corporation
   physical id:
                  1a.1
   bus info:
                  pci@0000:00:1a.1
   version:       03
   width:         32 bits
   clock:         33MHz
   capabilities:  uhci bus_master cap_list
   configuration:
                  driver  = uhci_hcd
                  latency = 0
   resources:
                  irq    : 21
                  ioport : 6f80(size=32)
   id:
                  usb:2
   description:   USB controller
   product:       82801I (ICH9 Family) USB UHCI Controller #6
   vendor:        Intel Corporation
   physical id:
                  1a.2
   bus info:
                  pci@0000:00:1a.2
   version:       03
   width:         32 bits
   clock:         33MHz
   capabilities:  uhci bus_master cap_list
   configuration:
                  driver  = uhci_hcd
                  latency = 0
   resources:
                  irq    : 22
                  ioport : 6fa0(size=32)
   id:
                  usb:3
   description:   USB controller
   product:       82801I (ICH9 Family) USB2 EHCI Controller #2
   vendor:        Intel Corporation
   physical id:
                  1a.7
   bus info:
                  pci@0000:00:1a.7
   version:       03
   width:         32 bits
   clock:         33MHz
   capabilities:  pm debug ehci bus_master cap_list
   configuration:
                  driver  = ehci_hcd
                  latency = 0
   resources:
                  irq    : 22
                  memory : fed1c400-fed1c7ff
   id:
                  multimedia
   description:   Audio device
   product:       82801I (ICH9 Family) HD Audio Controller
   vendor:        Intel Corporation
   physical id:
                  1b
   bus info:
                  pci@0000:00:1b.0
   version:       03
   width:         64 bits
   clock:         33MHz
   capabilities:  pm msi pciexpress bus_master cap_list
   configuration:
                  driver  = snd_hda_intel
                  latency = 0
   resources:
                  irq    : 47
                  memory : f6fdc000-f6fdffff
   id:
                  pci:1
   description:   PCI bridge
   product:       82801I (ICH9 Family) PCI Express Port 1
   vendor:        Intel Corporation
   physical id:
                  1c
   bus info:
                  pci@0000:00:1c.0
   version:       03
   width:         32 bits
   clock:         33MHz
   capabilities:  pci pciexpress msi pm normal_decode bus_master cap_list
   configuration:
                  driver = pcieport
   resources:
                  irq    : 41
                  ioport : 5000(size=4096)
                  memory : f0800000-f09fffff
                  ioport : f0a00000(size=2097152)
   id:
                  pci:2
   description:   PCI bridge
   product:       82801I (ICH9 Family) PCI Express Port 2
   vendor:        Intel Corporation
   physical id:
                  1c.1
   bus info:
                  pci@0000:00:1c.1
   version:       03
   width:         32 bits
   clock:         33MHz
   capabilities:  pci pciexpress msi pm normal_decode bus_master cap_list
   configuration:
                  driver = pcieport
   resources:
                  irq    : 42
                  ioport : 4000(size=4096)
                  memory : f1f00000-f1ffffff
                  ioport : f0600000(size=2097152)
   id:
                  network
   description:   Wireless interface
   product:       WiFi Link 5100
   vendor:        Intel Corporation
   physical id:
                  0
   bus info:
                  pci@0000:0c:00.0
   logical name:
                  wlan0
   version:       00
   serial:        [REMOVED]
   width:         64 bits
   clock:         33MHz
   capabilities:  pm msi pciexpress bus_master cap_list ethernet physical
                  wireless
   configuration:
                  broadcast     = yes
                  driver        = iwlwifi
                  driverversion = 3.2.0-55-generic
                  firmware      = 8.83.5.1 build 33692
                  latency       = 0
                  link          = no
                  multicast     = yes
                  wireless      = IEEE 802.11abgn
   resources:
                  irq    : 48
                  memory : f1ffe000-f1ffffff
   id:
                  pci:3
   description:   PCI bridge
   product:       82801I (ICH9 Family) PCI Express Port 3
   vendor:        Intel Corporation
   physical id:
                  1c.2
   bus info:
                  pci@0000:00:1c.2
   version:       03
   width:         32 bits
   clock:         33MHz
   capabilities:  pci pciexpress msi pm normal_decode bus_master cap_list
   configuration:
                  driver = pcieport
   resources:
                  irq    : 43
                  ioport : 3000(size=4096)
                  memory : f0200000-f03fffff
                  ioport : f0400000(size=2097152)
   id:
                  pci:4
   description:   PCI bridge
   product:       82801I (ICH9 Family) PCI Express Port 4
   vendor:        Intel Corporation
   physical id:
                  1c.3
   bus info:
                  pci@0000:00:1c.3
   version:       03
   width:         32 bits
   clock:         33MHz
   capabilities:  pci pciexpress msi pm normal_decode bus_master cap_list
   configuration:
                  driver = pcieport
   resources:
                  irq    : 44
                  ioport : c000(size=4096)
                  memory : f1c00000-f1efffff
                  ioport : f0000000(size=2097152)
   id:
                  usb:4
   description:   USB controller
   product:       82801I (ICH9 Family) USB UHCI Controller #1
   vendor:        Intel Corporation
   physical id:
                  1d
   bus info:
                  pci@0000:00:1d.0
   version:       03
   width:         32 bits
   clock:         33MHz
   capabilities:  uhci bus_master cap_list
   configuration:
                  driver  = uhci_hcd
                  latency = 0
   resources:
                  irq    : 20
                  ioport : 6f00(size=32)
   id:
                  usb:5
   description:   USB controller
   product:       82801I (ICH9 Family) USB UHCI Controller #2
   vendor:        Intel Corporation
   physical id:
                  1d.1
   bus info:
                  pci@0000:00:1d.1
   version:       03
   width:         32 bits
   clock:         33MHz
   capabilities:  uhci bus_master cap_list
   configuration:
                  driver  = uhci_hcd
                  latency = 0
   resources:
                  irq    : 21
                  ioport : 6f20(size=32)
   id:
                  usb:6
   description:   USB controller
   product:       82801I (ICH9 Family) USB UHCI Controller #3
   vendor:        Intel Corporation
   physical id:
                  1d.2
   bus info:
                  pci@0000:00:1d.2
   version:       03
   width:         32 bits
   clock:         33MHz
   capabilities:  uhci bus_master cap_list
   configuration:
                  driver  = uhci_hcd
                  latency = 0
   resources:
                  irq    : 22
                  ioport : 6f40(size=32)
   id:
                  usb:7
   description:   USB controller
   product:       82801I (ICH9 Family) USB2 EHCI Controller #1
   vendor:        Intel Corporation
   physical id:
                  1d.7
   bus info:
                  pci@0000:00:1d.7
   version:       03
   width:         32 bits
   clock:         33MHz
   capabilities:  pm debug ehci bus_master cap_list
   configuration:
                  driver  = ehci_hcd
                  latency = 0
   resources:
                  irq    : 20
                  memory : fed1c000-fed1c3ff
   id:
                 pci:5
   description:  PCI bridge
   product:      82801 Mobile PCI Bridge
   vendor:       Intel Corporation
   physical id:
                 1e
   bus info:
                 pci@0000:00:1e.0
   version:      93
   width:        32 bits
   clock:        33MHz
   capabilities: pci subtractive_decode bus_master cap_list
   resources:
                 ioport : 2000(size=4096)
                 memory : f1b00000-f1bfffff
   id:
                  pcmcia
   description:   CardBus bridge
   product:       RL5c476 II
   vendor:        Ricoh Co Ltd
   physical id:
                  1
   bus info:
                  pci@0000:03:01.0
   version:       ba
   width:         64 bits
   clock:         33MHz
   capabilities:  pcmcia bus_master cap_list
   configuration:
                  driver     = yenta_cardbus
                  latency    = 176
                  maxlatency = 5
                  mingnt     = 128
   resources:
                  iomemory : b00704030-b0070402f
                  irq      : 19
                  memory   : fc000000-fc000fff
                  ioport   : 2400(size=256)
                  ioport   : 2000(size=256)
                  memory   : f0c00000-f0ffffff
                  memory   : f1000000-f13fffff
   id:
                  firewire
   description:   FireWire (IEEE 1394)
   product:       R5C832 IEEE 1394 Controller
   vendor:        Ricoh Co Ltd
   physical id:
                  1.1
   bus info:
                  pci@0000:03:01.1
   version:       04
   width:         32 bits
   clock:         33MHz
   capabilities:  pm ohci bus_master cap_list
   configuration:
                  driver     = firewire_ohci
                  latency    = 64
                  maxlatency = 4
                  mingnt     = 2
   resources:
                  irq    : 17
                  memory : f1bff800-f1bfffff
   id:
                  generic
   description:   SD Host controller
   product:       R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
   vendor:        Ricoh Co Ltd
   physical id:
                  1.2
   bus info:
                  pci@0000:03:01.2
   version:       21
   width:         32 bits
   clock:         33MHz
   capabilities:  pm bus_master cap_list
   configuration:
                  driver  = sdhci-pci
                  latency = 64
   resources:
                  irq    : 18
                  memory : f1bff600-f1bff6ff
   id:
                  isa
   description:   ISA bridge
   product:       ICH9M-E LPC Interface Controller
   vendor:        Intel Corporation
   physical id:
                  1f
   bus info:
                  pci@0000:00:1f.0
   version:       03
   width:         32 bits
   clock:         33MHz
   capabilities:  isa bus_master cap_list
   configuration:
                  latency = 0
   id:
                  storage
   description:   RAID bus controller
   product:       82801 Mobile SATA Controller [RAID mode]
   vendor:        Intel Corporation
   physical id:
                  1f.2
   bus info:
                  pci@0000:00:1f.2
   logical name:
                  scsi0
   logical name:
                  scsi1
   version:       03
   width:         32 bits
   clock:         66MHz
   capabilities:  storage msi pm bus_master cap_list emulated
   configuration:
                  driver  = ahci
                  latency = 0
   resources:
                  irq    : 45
                  ioport : 6e70(size=8)
                  ioport : 6e78(size=4)
                  ioport : 6e80(size=8)
                  ioport : 6e88(size=4)
                  ioport : 6ea0(size=32)
                  memory : fed1c800-fed1cfff
   id:
                  disk
   description:   ATA Disk
   product:       ST9250410ASG
   vendor:        Seagate
   physical id:
                  0
   bus info:
                  scsi@0:0.0.0
   logical name:
                  /dev/sda
   version:       0003
   serial:        [REMOVED]
   size:          232GiB (250GB)
   capabilities:  partitioned partitioned:dos
   configuration:
                  ansiversion = 5
                  signature   = 00001278
   id:
   volume:0
   description: EXT4 volume
   vendor: Linux
   physical id:
   1
   bus info:
   scsi@0:0.0.0,1
   logical name:
   /dev/sda1
   logical name:
   /
   version: 1.0
   serial: [REMOVED]
   size: 228GiB
   capacity: 228GiB
   capabilities: primary bootable journaled extended_attributes
   large_files huge_files dir_nlink recover extents ext4 ext2 initialized
   configuration:
created        = 2013-03-13 15:03:35
filesystem     = ext4
lastmountpoint = /
modified       = 2013-03-13 14:18:35
mount.fstype   = ext4
mount.options  =
                 rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered
mounted        = 2013-10-24 08:38:30
state          = mounted
   id:
                 volume:1
   description:  Extended partition
   physical id:
                 2
   bus info:
                 scsi@0:0.0.0,2
   logical name:
                 /dev/sda2
   size:         4083MiB
   capacity:     4083MiB
   capabilities: primary extended partitioned partitioned:extended
   id:
                 logicalvolume
   description:  Linux swap / Solaris partition
   physical id:
                 5
   logical name:
                 /dev/sda5
   capacity:     4083MiB
   capabilities: nofs
   id:
                  cdrom
   description:   DVD-RAM writer
   product:       DVD+-RW TS-U633F
   vendor:        TSSTcorp
   physical id:
                  1
   bus info:
                  scsi@1:0.0.0
   logical name:
                  /dev/cdrom1
   logical name:
                  /dev/cdrw1
   logical name:
                  /dev/dvd1
   logical name:
                  /dev/dvdrw1
   logical name:
                  /dev/sr0
   version:       D200
   capabilities:  removable audio cd-r cd-rw dvd dvd-r dvd-ram
   configuration:
                  ansiversion = 5
                  status      = nodisc
   id:
                  serial
   description:   SMBus
   product:       82801I (ICH9 Family) SMBus Controller
   vendor:        Intel Corporation
   physical id:
                  1f.3
   bus info:
                  pci@0000:00:1f.3
   version:       03
   width:         64 bits
   clock:         33MHz
   configuration:
                  latency = 0
   resources:
                  memory : f6fdaf00-f6fdafff
                  ioport : 1100(size=32)

   id:
                  battery
   product:       DELL MP49299
   vendor:        SMP
   physical id:
                  1
   slot:          Sys. Battery Bay
   capacity:      78000mWh
   configuration:
                  voltage = 11,1V

   id:
                  network
   description:   Ethernet interface
   physical id:
                  2
   logical name:
                  wwan0
   serial:        [REMOVED]
   capabilities:  ethernet physical
   configuration:
                  broadcast     = yes
                  driver        = cdc_ether
                  driverversion = 22-Aug-2005
                  firmware      = Mobile Broadband Network Device
                  link          = no
                  multicast     = yes

```

---

