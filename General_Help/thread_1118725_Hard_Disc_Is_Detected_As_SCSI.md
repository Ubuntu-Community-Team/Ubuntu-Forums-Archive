---
title: "Hard Disc Is Detected As SCSI"
date: 2009-04-07
forum: General Help
---

### Post by ravi_buz on 2009-04-07
I amm new to linux and starting to love it. I have installed ubuntu 8.10 and removed it as it had many bugs and installed 8.04 but now my HDD which is connected with ide cable is detected as an SCSI drive and i am unbable to use it . Can some one help me mount this into ubuntu (i dint have this problem even when i booted using ubuntu 8.10 live cd)

---

### Post by rbc on 2009-04-07
I cannot help, but the fact that your ide drive is being seen as a SCSI drive is perfectly normal. I read somewhere, a while back, that the driver support for SCSI was better, hence the switch. Maybe Linux does not like your motherboard? Post back with more details about your hardware and maybe someone else can help

---

### Post by nebileix on 2009-04-07
pls do

```
$ sudo lshw
$ sudo dmesg
```

and post it here in order for ppl to help u.

---

### Post by ravi_buz on 2009-04-08
ravi@Ravi-desktop:~$ sudo lshw
ravi-desktop              
    description: Desktop Computer
    product: PVM7
    vendor: Kobian
    version: 1.0
    serial: 00000000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: PVM7
       vendor: Kobian
       physical id: 0
       version: 1.0
       serial: 00000000
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080012 (03/08/2006)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.4.9
          serial: 0000-0F49-0000-0000-0000-0000
          slot: CPU 1
          size: 2793MHz
          capacity: 2793MHz
          width: 64 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe x86-64 constant_tsc up pebs bts sync_rdtsc pni monitor ds_cpl tm2 cid cx16 xtpr lahf_lm
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: internal write-back unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
     *-memory
          description: System Memory
          physical id: 27
          slot: System board or motherboard
          size: 768MiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 256MiB
             width: 64 bits
     *-pci:0
          description: Host bridge
          product: CN700/VN800/P4M800CE/Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via latency=8 module=via_agp
        *-pci
             description: PCI bridge
             product: VT8237 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: NV34 [GeForce FX 5200]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
        *-ide:0
             description: IDE interface
             product: VIA VT6420 SATA RAID Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             logical name: scsi2
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=sata_via latency=64 module=sata_via
           *-disk
                description: ATA Disk
                product: ST3160815AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sdb
                version: 4.AA
                serial: 6RAE2K19
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=2c892c89
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /media/media1
                   version: 3.1
                   serial: dcac01ad-64b6-6f40-a4b1-e806a81cf192
                   size: 29GiB
                   capacity: 29GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2006-03-10 03:56:45 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,noatime,relatime,user_id=0,group_id=0,allow_other state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sdb2
                   size: 107GiB
                   capacity: 107GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sdb5
                      logical name: /media/media2
                      capacity: 40GiB
                      configuration: mount.fstype=fuseblk mount.options=rw,nosuid,nodev,noatime,relatime,user_id=0,group_id=0,allow_other state=mounted
                 *-logicalvolume:1
                      description: HPFS/NTFS partition
                      physical id: 6
                      logical name: /dev/sdb6
                      logical name: /media/media3
                      capacity: 40GiB
                      configuration: mount.fstype=fuseblk mount.options=rw,nosuid,nodev,noatime,relatime,user_id=0,group_id=0,allow_other state=mounted
                 *-logicalvolume:2
                      description: HPFS/NTFS partition
                      physical id: 7
                      logical name: /dev/sdb7
                      logical name: /media/media4
                      capacity: 27GiB
                      configuration: mount.fstype=fuseblk mount.options=rw,nosuid,nodev,noatime,relatime,user_id=0,group_id=0,allow_other state=mounted
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sdb3
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 225820f5-7867-4e4e-aeaf-c1e40ae818a2
                   size: 11GiB
                   capacity: 11GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-03-20 21:39:57 filesystem=ext3 modified=2009-04-08 13:05:57 mount.fstype=ext3 mount.options=rw,relatime,data=ordered mounted=2009-04-08 13:05:57 state=mounted
              *-volume:3
                   description: Linux swap volume
                   physical id: 4
                   bus info: scsi@2:0.0.0,4
                   logical name: /dev/sdb4
                   version: 1
                   serial: 11aab801-ef3f-4ffb-95c6-db987c049044
                   size: 1953MiB
                   capacity: 1953MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
        *-ide:1
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             logical name: scsi0
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32 module=pata_via
           *-disk
                description: ATA Disk
                product: SAMSUNG SP0411N
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: TW10
                serial: S01JJ10L674222
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=42170123
              *-volume UNCLAIMED
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   version: 3.1
                   serial: 42aa2185-e5c4-4e94-81d9-350fb2ffe5f5
                   size: 37GiB
                   capacity: 37GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2009-04-04 22:19:58 filesystem=ntfs state=clean
           *-cdrom:0
                description: DVD-RAM writer
                product: DVD-RAM GSA-H55N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/dvd1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.05
                serial: [HL-DT-STDVD-RAM GSA-H55N1.0507/12/11 7U02
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open
           *-cdrom:1
                description: DVD reader
                product: RW/DVD GCC-4522B
                vendor: HL-DT-ST
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 1.08
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=open
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-isa
             description: ISA bridge
             product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 60
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 78
             serial: 00:16:ec:9b:6b:c7
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=115.98.37.85 latency=64 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
     *-pci:1
          description: Host bridge
          product: CN700/VN800/P4M800CE/Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: CN700/VN800/P4M800CE/Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: PT890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: CN700/VN800/P4M800CE/Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: CN700/VN800/P4M800CE/Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz

---

### Post by ravi_buz on 2009-04-08
output of lshw sorry unable to see the full output in terminal

19.771055] CPU: L2 cache: 1024K
[   19.771059] CPU: Hyper-Threading is disabled
[   19.771061] CPU: After all inits, caps: bfebfbff 20000000 00000000 0000b180 0000651d 00000000 00000001 00000000
[   19.771073] Compat vDSO mapped to ffffe000.
[   19.771091] Checking 'hlt' instruction... OK.
[   19.787324] SMP alternatives: switching to UP code
[   19.789387] Freeing SMP alternatives: 11k freed
[   19.789523] Early unpacking initramfs... done
[   20.105490] ACPI: Core revision 20070126
[   20.105555] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   20.108259] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 09
[   20.108307] Total of 1 processors activated (5594.31 BogoMIPS).
[   20.109070] ENABLING IO-APIC IRQs
[   20.109405] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   20.254074] Brought up 1 CPUs
[   20.254136] CPU0 attaching sched-domain:
[   20.254140]  domain 0: span 01
[   20.254143]   groups: 01
[   20.254360] net_namespace: 64 bytes
[   20.254369] Booting paravirtualized kernel on bare hardware
[   20.255042] Time: 13:05:35  Date: 04/08/09
[   20.255076] NET: Registered protocol family 16
[   20.255332] EISA bus registered
[   20.255372] ACPI: bus type pci registered
[   20.255615] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[   20.255618] PCI: Using configuration type 1
[   20.255627] Setting up standard PCI resources
[   20.273025] ACPI: EC: Look up EC in DSDT
[   20.279206] ACPI: Interpreter enabled
[   20.279209] ACPI: (supports S0 S1 S3 S4 S5)
[   20.279228] ACPI: Using IOAPIC for interrupt routing
[   20.290297] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   20.291598] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   20.291805] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   20.301880] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   20.302011] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   20.302132] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   20.302251] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   20.302372] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   20.302493] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   20.302613] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   20.302734] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   20.302870] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  FD, should be F0 [20070126]
[   20.302877] Linux Plug and Play Support v0.97 (c) Adam Belay
[   20.302918] pnp: PnP ACPI init
[   20.302927] ACPI: bus type pnp registered
[   20.310423] pnp: PnP ACPI: found 14 devices
[   20.310425] ACPI: ACPI bus type pnp unregistered
[   20.310430] PnPBIOS: Disabled by ACPI PNP
[   20.310723] PCI: Using ACPI for IRQ routing
[   20.310726] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   20.329908] NET: Registered protocol family 8
[   20.329910] NET: Registered protocol family 20
[   20.329999] AppArmor: AppArmor Filesystem Enabled
[   20.333892] Time: tsc clocksource has been installed.
[   20.341931] system 00:09: ioport range 0xa00-0xa0f has been reserved
[   20.341935] system 00:09: ioport range 0x290-0x29f has been reserved
[   20.341937] system 00:09: ioport range 0xa20-0xa2f has been reserved
[   20.341940] system 00:09: ioport range 0xa30-0xa3f has been reserved
[   20.341942] system 00:09: ioport range 0xa40-0xa4f has been reserved
[   20.341948] system 00:0a: ioport range 0x290-0x297 has been reserved
[   20.341951] system 00:0a: ioport range 0xc00-0xc05 has been reserved
[   20.341953] system 00:0a: ioport range 0x3e0-0x3e7 has been reserved
[   20.341956] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[   20.341959] system 00:0a: ioport range 0x800-0x87f has been reserved
[   20.341961] system 00:0a: ioport range 0x400-0x41f has been reserved
[   20.341968] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[   20.341971] system 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
[   20.341978] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[   20.341980] system 00:0d: iomem range 0xc0000-0xcffff could not be reserved
[   20.341983] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[   20.341986] system 00:0d: iomem range 0x100000-0x2fffffff could not be reserved
[   20.341989] system 00:0d: iomem range 0xfff80000-0xffffffff has been reserved
[   20.372453] PCI: Bridge: 0000:00:01.0
[   20.372455]   IO window: disabled.
[   20.372461]   MEM window: fca00000-feafffff
[   20.372466]   PREFETCH window: d7f00000-f7efffff
[   20.372493] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   20.372506] NET: Registered protocol family 2
[   20.409863] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   20.410303] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   20.411307] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   20.412142] TCP: Hash tables configured (established 131072 bind 65536)
[   20.412145] TCP reno registered
[   20.421964] checking if image is initramfs... it is
[   20.873013] Switched to high resolution mode on CPU 0
[   21.043481] Freeing initrd memory: 7306k freed
[   21.044289] audit: initializing netlink socket (disabled)
[   21.044307] audit(1239195936.248:1): initialized
[   21.046725] VFS: Disk quotas dquot_6.5.1
[   21.046812] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   21.046969] io scheduler noop registered
[   21.046972] io scheduler anticipatory registered
[   21.046974] io scheduler deadline registered
[   21.046987] io scheduler cfq registered (default)
[   21.047003] PCI: VIA PCI bridge detected. Disabling DAC.
[   21.047078] PCI: Bypassing VIA 8237 APIC De-Assert Message
[   21.047103] Boot video device is 0000:01:00.0
[   21.047433] isapnp: Scanning for PnP cards...
[   21.399035] isapnp: No Plug & Play device found
[   21.435606] Real Time Clock Driver v1.12ac
[   21.435738] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   21.435872] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   21.436854] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   21.437745] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   21.437828] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   21.437950] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   21.438377] serio: i8042 KBD port at 0x60,0x64 irq 1
[   21.438384] serio: i8042 AUX port at 0x60,0x64 irq 12
[   21.444177] mice: PS/2 mouse device common for all mice
[   21.444317] EISA: Probing bus 0 at eisa.0
[   21.444360] EISA: Detected 0 cards.
[   21.444364] cpuidle: using governor ladder
[   21.444366] cpuidle: using governor menu
[   21.444462] NET: Registered protocol family 1
[   21.444495] Using IPI No-Shortcut mode
[   21.444533] registered taskstats version 1
[   21.444635]   Magic number: 5:478:78
[   21.444769] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   21.444771] EDD information not available.
[   21.445203] Freeing unused kernel memory: 368k freed
[   21.471967] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   22.662159] fuse init (API version 7.9)
[   22.738378] ACPI Error (tbinstal-0134): Table has invalid signature [  &#65533;], must be SSDT, PSDT or OEMx [20070126]
[   22.738391] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU1._PDC] (Node ee0c3150), AE_BAD_SIGNATURE
[   22.738482] ACPI: Processor [CPU1] (supports 16 throttling states)
[   22.739223] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   22.739237] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   22.739250] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   23.347563] SCSI subsystem initialized
[   23.428613] libata version 3.00 loaded.
[   23.436655] usbcore: registered new interface driver usbfs
[   23.436688] usbcore: registered new interface driver hub
[   23.455783] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 16
[   23.455869] ACPI: PCI interrupt for device 0000:00:0f.0 disabled
[   23.455899] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 16
[   23.455929] ACPI: PCI interrupt for device 0000:00:0f.1 disabled
[   23.464582] usbcore: registered new device driver usb
[   23.468602] pata_via 0000:00:0f.1: version 0.3.3
[   23.468634] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 16
[   23.482181] scsi0 : pata_via
[   23.508692] scsi1 : pata_via
[   23.510932] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[   23.510936] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[   23.511746] USB Universal Host Controller Interface driver v3.0
[   23.527465] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   23.593073] Floppy drive(s): fd0 is 1.44M
[   23.612745] FDC 0 is a post-1991 82077
[   23.672666] ata1.00: ATA-7: SAMSUNG SP0411N, TW100-13, max UDMA/100
[   23.672672] ata1.00: 78242976 sectors, multi 16: LBA48 
[   23.680507] ata1.00: configured for UDMA/100
[   24.179738] ata2.00: ATAPI: HL-DT-STDVD-RAM GSA-H55N, 1.05, max UDMA/66
[   24.179769] ata2.01: ATAPI: HL-DT-ST RW/DVD GCC-4522B, 1.08, max UDMA/33
[   24.351314] ata2.00: configured for UDMA/66
[   24.538908] ata2.01: configured for UDMA/33
[   24.539066] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG SP0411N  TW10 PQ: 0 ANSI: 5
[   24.540834] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GSA-H55N 1.05 PQ: 0 ANSI: 5
[   24.541836] scsi 1:0:1:0: CD-ROM            HL-DT-ST RW/DVD GCC-4522B 1.08 PQ: 0 ANSI: 5
[   24.545672] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 17
[   24.545690] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   24.546001] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   24.546037] uhci_hcd 0000:00:10.0: irq 17, io base 0x0000dc00
[   24.546193] usb usb1: configuration #1 chosen from 1 choice
[   24.546223] hub 1-0:1.0: USB hub found
[   24.546231] hub 1-0:1.0: 2 ports detected
[   24.558446] Driver 'sd' needs updating - please use bus_type methods
[   24.558573] sd 0:0:0:0: [sda] 78242976 512-byte hardware sectors (40060 MB)
[   24.558591] sd 0:0:0:0: [sda] Write Protect is off
[   24.558594] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.558619] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   24.558763] sd 0:0:0:0: [sda] 78242976 512-byte hardware sectors (40060 MB)
[   24.558777] sd 0:0:0:0: [sda] Write Protect is off
[   24.558780] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.558802] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   24.558807]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   24.570770] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   24.570776] ata1.00: BMDMA stat 0x24
[   24.570783] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   24.570784]          res 51/84:00:07:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[   24.570788] ata1.00: status: { DRDY ERR }
[   24.570790] ata1.00: error: { ICRC ABRT }
[   24.570822] ata1: soft resetting link
[   24.646620] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 17
[   24.646636] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   24.646666] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   24.646693] uhci_hcd 0000:00:10.1: irq 17, io base 0x0000d880
[   24.646826] usb usb2: configuration #1 chosen from 1 choice
[   24.646856] hub 2-0:1.0: USB hub found
[   24.646864] hub 2-0:1.0: 2 ports detected
[   24.742654] ata1.00: configured for UDMA/100
[   24.742669] ata1: EH complete
[   24.750423] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 17
[   24.750436] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   24.750471] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   24.750497] uhci_hcd 0000:00:10.2: irq 17, io base 0x0000d800
[   24.750624] usb usb3: configuration #1 chosen from 1 choice
[   24.750652] hub 3-0:1.0: USB hub found
[   24.750659] hub 3-0:1.0: 2 ports detected
[   24.753693] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   24.753698] ata1.00: BMDMA stat 0x24
[   24.753705] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   24.753707]          res 51/84:00:07:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[   24.753710] ata1.00: status: { DRDY ERR }
[   24.753712] ata1.00: error: { ICRC ABRT }
[   24.753738] ata1: soft resetting link
[   24.854243] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 17
[   24.854257] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   24.854289] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   24.854314] uhci_hcd 0000:00:10.3: irq 17, io base 0x0000d480
[   24.854438] usb usb4: configuration #1 chosen from 1 choice
[   24.854465] hub 4-0:1.0: USB hub found
[   24.854472] hub 4-0:1.0: 2 ports detected
[   24.922338] ata1.00: configured for UDMA/100
[   24.922358] ata1: EH complete
[   24.928311] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   24.928315] ata1.00: BMDMA stat 0x24
[   24.928323] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   24.928324]          res 51/84:00:07:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[   24.928327] ata1.00: status: { DRDY ERR }
[   24.928329] ata1.00: error: { ICRC ABRT }
[   24.928352] ata1: soft resetting link
[   24.958422] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 17
[   24.958440] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   24.958475] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   24.958522] ehci_hcd 0000:00:10.4: irq 17, io mem 0xfebffc00
[   24.969966] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   24.970132] usb usb5: configuration #1 chosen from 1 choice
[   24.970166] hub 5-0:1.0: USB hub found
[   24.970174] hub 5-0:1.0: 8 ports detected
[   25.074002] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 18
[   25.078216] eth0: VIA Rhine II at 0xfebff800, 00:16:ec:9b:6b:c7, IRQ 18.
[   25.078927] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 45e1.
[   25.079016] sata_via 0000:00:0f.0: version 2.3
[   25.079027] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 16
[   25.079076] sata_via 0000:00:0f.0: routed to hard irq line 11
[   25.080109] scsi2 : sata_via
[   25.080660] scsi3 : sata_via
[   25.082296] ata3: SATA max UDMA/133 cmd 0xec00 ctl 0xe880 bmdma 0xe400 irq 16
[   25.082300] ata4: SATA max UDMA/133 cmd 0xe800 ctl 0xe480 bmdma 0xe408 irq 16
[   25.098074] ata1.00: configured for UDMA/100
[   25.098099] ata1: EH complete
[   25.102943] ata1.00: limiting speed to UDMA/66:PIO4
[   25.102948] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   25.102953] ata1.00: BMDMA stat 0x24
[   25.102959] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   25.102961]          res 51/84:00:07:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[   25.102964] ata1.00: status: { DRDY ERR }
[   25.102966] ata1.00: error: { ICRC ABRT }
[   25.102997] ata1: soft resetting link
[   25.273734] ata1.00: configured for UDMA/66
[   25.273749] ata1: EH complete
[   25.277556] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   25.277560] ata1.00: BMDMA stat 0x24
[   25.277566] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   25.277567]          res 51/84:00:07:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[   25.277570] ata1.00: status: { DRDY ERR }
[   25.277572] ata1.00: error: { ICRC ABRT }
[   25.277595] ata1: soft resetting link
[   25.285382] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   25.457419] ata1.00: configured for UDMA/66
[   25.457431] ata1: EH complete
[   25.468809] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   25.468813] ata1.00: BMDMA stat 0x24
[   25.468819] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   25.468820]          res 51/84:00:07:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[   25.468823] ata1.00: status: { DRDY ERR }
[   25.468825] ata1.00: error: { ICRC ABRT }
[   25.468848] ata1: soft resetting link
[   25.489326] ata3.00: ATA-7: ST3160815AS, 4.AAB, max UDMA/133
[   25.489330] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   25.555873] ata3.00: configured for UDMA/133
[   25.637112] ata1.00: configured for UDMA/66
[   25.637126] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   25.637131] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[   25.637137] Descriptor sense data with sense descriptors (in hex):
[   25.637139]         72 0b 47 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   25.637147]         00 00 00 07 
[   25.637151] sd 0:0:0:0: [sda] Add. Sense: Scsi parity error
[   25.637158] end_request: I/O error, dev sda, sector 0
[   25.637163] Buffer I/O error on device sda, logical block 0
[   25.637181] ata1: EH complete
[   25.643431] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   25.643435] ata1.00: BMDMA stat 0x24
[   25.643441] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   25.643442]          res 51/84:00:07:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[   25.643445] ata1.00: status: { DRDY ERR }
[   25.643447] ata1.00: error: { ICRC ABRT }
[   25.643470] ata1: soft resetting link
[   25.756570] ata4: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   25.766861] scsi 2:0:0:0: Direct-Access     ATA      ST3160815AS      4.AA PQ: 0 ANSI: 5
[   25.812814] ata1.00: configured for UDMA/66
[   25.812836] ata1: EH complete
[   25.818058] ata1.00: limiting speed to UDMA/33:PIO4
[   25.818062] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   25.818067] ata1.00: BMDMA stat 0x24
[   25.818074] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   25.818075]          res 51/84:00:07:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[   25.818078] ata1.00: status: { DRDY ERR }
[   25.818080] ata1.00: error: { ICRC ABRT }
[   25.818104] ata1: soft resetting link
[   25.988504] ata1.00: configured for UDMA/33
[   25.988514] ata1: EH complete
[   25.992540] ldm_validate_partition_table(): Disk read failed.
[   25.992550] Dev sda: unable to read RDB block 0
[   25.992635] sd 0:0:0:0: [sda] 78242976 512-byte hardware sectors (40060 MB)
[   25.992830] sd 0:0:0:0: [sda] Write Protect is off
[   25.992833] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   25.992861] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   25.992887] sd 0:0:0:0: [sda] 78242976 512-byte hardware sectors (40060 MB)
[   25.992900] sd 0:0:0:0: [sda] Write Protect is off
[   25.992903] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   25.992925] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   25.992933]  unable to read partition table
[   25.993002] sd 0:0:0:0: [sda] Attached SCSI disk
[   25.994169] sd 2:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   25.994186] sd 2:0:0:0: [sdb] Write Protect is off
[   25.994189] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   25.994213] sd 2:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   25.994276] sd 2:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   25.994290] sd 2:0:0:0: [sdb] Write Protect is off
[   25.994293] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   25.994316] sd 2:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   25.994320]  sdb:sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   25.999799] Uniform CD-ROM driver Revision: 3.20
[   25.999854] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   26.002700] sr1: scsi3-mmc drive: 52x/52x writer cd/rw xa/form2 cdda tray
[   26.002742] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   26.011313]  sdb1 sdb2 < sdb5 sdb6 sdb7 > sdb3 sdb4
[   26.066635] sd 2:0:0:0: [sdb] Attached SCSI disk
[   26.083189] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   26.083221] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   26.083246] sr 1:0:1:0: Attached scsi generic sg2 type 5
[   26.083273] sd 2:0:0:0: Attached scsi generic sg3 type 0
[   26.147931] usb 4-1: new full speed USB device using uhci_hcd and address 2
[   26.303978] usb 4-1: configuration #1 chosen from 1 choice
[   26.642679] Attempting manual resume
[   26.642685] swsusp: Resume From Partition 8:20
[   26.642687] PM: Checking swsusp image.
[   26.642868] PM: Resume from disk failed.
[   26.681479] kjournald starting.  Commit interval 5 seconds
[   26.681494] EXT3-fs: mounted filesystem with ordered data mode.
[   36.378426] Linux agpgart interface v0.102
[   36.454261] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   36.494275] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   36.582059] agpgart: Detected VIA VT3314 chipset
[   36.587406] agpgart: AGP aperture is 64M @ 0xf8000000
[   36.872086] input: Power Button (FF) as /devices/virtual/input/input2
[   36.885450] ACPI: Power Button (FF) [PWRF]
[   36.885637] input: Sleep Button (CM) as /devices/virtual/input/input3
[   36.897614] ACPI: Sleep Button (CM) [SLPB]
[   36.897740] input: Power Button (CM) as /devices/virtual/input/input4
[   36.909389] ACPI: Power Button (CM) [PWRB]
[   38.338316] nvidia: module license 'NVIDIA' taints kernel.
[   39.013809] Linux video capture interface: v2.00
[   39.064996] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   39.153482] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.47
[   39.154754] usb 4-1: SN9C120 PC Camera Controller detected (vid:pid 0x0C45:0x613C)
[   39.264525] usb 4-1: No supported image sensor detected for this bridge
[   39.264576] usbcore: registered new interface driver sn9c102
[   39.462163] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found. SONIX JPEG (sn9c1xx) 
[   39.469139] usbcore: registered new interface driver gspca
[   39.469147] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.20 registered
[   39.504462] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 19
[   39.504613] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   40.017567] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 20
[   40.017945] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   40.183908] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[   40.218693] parport_pc 00:08: reported by Plug and Play ACPI
[   40.218773] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   41.513013] lp0: using parport0 (interrupt-driven).
[   41.567204] Adding 2000084k swap on /dev/sdb4.  Priority:-1 extents:1 across:2000084k
[   42.136300] EXT3 FS on sdb3, internal journal
[   43.932767] ip_tables: (C) 2000-2006 Netfilter Core Team
[   44.343096] No dock devices found.
[   45.446277] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   45.446284] apm: overridden by ACPI.
[   45.553186] ppdev: user-space parallel port driver
[   45.675342] audit(1239176161.276:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4987 profile="/usr/sbin/cupsd" namespace="default"
[   48.496650] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   48.609968] Bluetooth: Core ver 2.11
[   48.610789] NET: Registered protocol family 31
[   48.610795] Bluetooth: HCI device and connection manager initialized
[   48.610800] Bluetooth: HCI socket layer initialized
[   48.633275] Bluetooth: L2CAP ver 2.9
[   48.633282] Bluetooth: L2CAP socket layer initialized
[   48.686685] Bluetooth: RFCOMM socket layer initialized
[   48.686705] Bluetooth: RFCOMM TTY layer initialized
[   48.686708] Bluetooth: RFCOMM ver 1.8
[   50.614882] NET: Registered protocol family 17
[   50.799449] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   50.799472] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   50.799551] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   52.948789] NET: Registered protocol family 10
[   52.949391] lo: Disabled Privacy Extensions
[   63.682871] eth0: no IPv6 routers present
[  561.559672] scorched3dc[13472]: segfault at 00000005 eip b7989de0 esp bf96f0b0 error 4
[ 3112.493779] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (7)
[ 3112.960352] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (9)
[ 3112.960493] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (14)
[ 3112.960623] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (13)
[ 3112.960752] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (16)
[ 3112.960882] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (11)
[ 3112.961012] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (6)
[ 3115.888807] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (7)
[ 3115.958727] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (9)
[ 3115.958866] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (14)
[ 3115.958997] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (13)
[ 3115.959126] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (16)
[ 3115.959256] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (11)
[ 3115.959385] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (6)
[ 3160.536865] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (7)
[ 3160.957617] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (9)
[ 3160.957759] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (14)
[ 3160.957891] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (13)
[ 3160.958024] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (16)
[ 3160.958156] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (11)
[ 3160.958288] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (6)
[ 3179.054898] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (7)
[ 3179.469731] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (9)
[ 3179.469873] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (14)
[ 3179.470006] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (13)
[ 3179.470138] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (16)
[ 3179.470270] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (11)
[ 3179.470402] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (6)
[ 3190.850573] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (7)
[ 3191.278855] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (9)
[ 3191.278998] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (14)
[ 3191.279130] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (13)
[ 3191.279262] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (16)
[ 3191.279394] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (11)
[ 3191.279526] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (6)
[ 3201.305016] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (7)
[ 3201.723392] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (9)
[ 3201.723531] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (14)
[ 3201.723661] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (13)
[ 3201.723791] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (16)
[ 3201.723921] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (11)
[ 3201.724051] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (6)
[ 3223.238725] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (7)
[ 3223.681487] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (9)
[ 3223.681627] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (14)
[ 3223.681758] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (13)
[ 3223.681888] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (16)
[ 3223.682024] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (11)
[ 3223.682155] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (6)
[ 5205.906488] scorched3dc[9812]: segfault at 00000005 eip b7989de0 esp bfd35e10 error 4
[ 5317.371138] scorched3dc[11357]: segfault at 00000005 eip b79a3de0 esp bfe84d60 error 4

---

### Post by WatchingThePain on 2009-04-08
Hmm I know it's normal for sata drives to show up as scsi.
Is there a sata connection available on the drive?.
Plus if there are any jumpers on the drive you might want to try removing.
I've noticed 'unable to read partition table' in the above post.

---

### Post by bumanie on 2009-04-08
As of (from memory), ubuntu 7.10, all hard drives have been designated /dev/sdx, prior to this, IDE drives were designated /dev/hdx whilst SATA and SCSI were designated /dev/sdx But this has not been the case for about 18 months

---

### Post by ravi_buz on 2009-04-08
I have one in SATA and another in IDE and both worked perfectly in ubuntu 8.10 as well as in live cd of kubuntu 8.10 and is working good in windows

---

### Post by Tony Flury on 2009-04-08
As an aside - in future - when posting the output of command, it can be very useful to include them in code or php tags (see the # or php icons in the little toolbar).

That way formatting is maintained.

---

### Post by mcduck on 2009-04-08
> **bumanie said:**
> As of (from memory), ubuntu 7.10, all hard drives have been designated /dev/sdx, prior to this, IDE drives were designated /dev/hdx whilst SATA and SCSI were designated /dev/sdx But this has not been the case for about 18 months

All recent Linux distributions use now the same driver for all PATA/SATA/SCSI drives, since the developers noticed that the SATA/SCSI driver handles PATA drives better than the old PATA driver did.

becasue of this they will also all use the same naming scheme (/dev/sdx as opposed to the old /dev/hdx of the PATA driver).

If the drive doesn't work, or it's not accessible, it's because of some other reason.

What drive is it? I can see two detected hard disks in the lshw output, one 160GB Seagate drive (dev/sdb, which contains your root partition) and one 40GB Samsung drive (/dev/sda/, which doesn't seem to be mounted). Is the drive in question this 40GB drive or some other?

---

### Post by ravi_buz on 2009-04-08
Yes i am having the problem with the 40 gb samsung HDD only

---

### Post by ravi_buz on 2009-04-09
Problem solved thanks to all for replying , I just removed ll the HDD and CD drives and connected one by one and restarted the system and the problem was solved

---

