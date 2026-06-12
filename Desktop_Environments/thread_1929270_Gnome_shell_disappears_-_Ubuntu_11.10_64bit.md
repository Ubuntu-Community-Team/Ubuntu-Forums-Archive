---
title: "Gnome shell disappears - Ubuntu 11.10 64bit"
date: 2012-02-21
forum: Desktop Environments
---

### Post by fubofo on 2012-02-21
Hi guys,

I have a strange issue whereby GNOME shell (3) randomly disappears / reloads . I have no idea what causes this or how to find out what is going on. It's almost like it is reloading for no reason. Again this is very sporadic so I cannot test.

When I say 'disappear' I mean all windows vanish, screenlets vanish then reload in wrong place, Docky vanishes, desktop icons vanish. Also on very few occasions GNOME shell seems to slow down a little, like when bumping Activities, it seems to lag a little before showing overlay.

**lshw**
```
kaipee@zoostorm-ubuntu:~$ sudo lshw
[sudo] password for kaipee: 
zoostorm-ubuntu           
    description: Desktop Computer
    product: OEM ()
    vendor: OEM
    version: OEM
    serial: OEM
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall32
    configuration: boot=normal chassis=desktop uuid=0673215F-1DED-48D1-F4AB-00016C644B29
  *-core
       description: Motherboard
       product: G31MX Series
       vendor: Foxconn
       physical id: 0
       serial: UY30932113570
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG
          date: 05/05/2009
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Quad CPU    Q9550  @ 2.83GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Quad CPU
          slot: Socket 775
          size: 3400MHz
          capacity: 4GHz
          width: 64 bits
          clock: 400MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
        *-cache
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: 24
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM Synchronous 50410 MHz (0.0 ns)
             physical id: 0
             slot: A0
             size: 2GiB
             width: 64 bits
             clock: 3165MHz (0.3ns)
        *-bank:1
             description: DIMM Synchronous 50410 MHz (0.0 ns)
             physical id: 1
             slot: A1
             size: 2GiB
             width: 64 bits
             clock: 3165MHz (0.3ns)
     *-pci
          description: Host bridge
          product: 82G33/G31/P35/P31 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82G33/G31/P35/P31 Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:b000(size=4096) memory:f8000000-fbffffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G92 [GeForce 9800 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:fa000000-faffffff memory:d0000000-dfffffff memory:f8000000-f9ffffff ioport:bf00(size=128) memory:fb000000-fb01ffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:44 memory:fdff8000-fdffbfff
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:d000(size=4096) memory:fdb00000-fdbfffff ioport:fde00000(size=1048576)
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:c000(size=4096) memory:fdd00000-fddfffff ioport:fdc00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 03
                serial: 00:01:6c:64:4b:29
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:43 ioport:ce00(size=256) memory:fdcff000-fdcfffff memory:fdcf8000-fdcfbfff memory:fdc00000-fdc1ffff
        *-usb:0
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:ff00(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:fe00(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:fd00(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:fc00(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fdfff000-fdfff3ff
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:e000(size=4096) memory:fda00000-fdafffff ioport:fd900000(size=1048576)
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fb00(size=16)
        *-ide:1
             description: IDE interface
             product: N10/ICH7 Family SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:fa00(size=8) ioport:f900(size=4) ioport:f800(size=8) ioport:f700(size=4) ioport:f600(size=16)
           *-disk
                description: ATA Disk
                product: SAMSUNG HD103UJ
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 1AA0
                serial: S13PJDWS753065
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=adb9e46a
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /media/Win7
                   version: 3.1
                   serial: 2e80579a-15dd-0f41-b935-480e556dbdb7
                   size: 147GiB
                   capacity: 147GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-11-22 16:10:10 filesystem=ntfs label=Win7 mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /media/Files
                   version: 3.1
                   serial: 867a096f-fc4b-b340-84bb-d8d81bd08610
                   size: 629GiB
                   capacity: 629GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=512 created=2009-11-24 17:42:41 filesystem=ntfs label=Files mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other state=mounted
              *-volume:2
                   description: Linux filesystem partition
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /boot
                   version: 1.0
                   serial: 3af46017-14fa-4e84-b1d7-ee6fd8add925
                   size: 476MiB
                   capacity: 476MiB
                   capabilities: primary ext2 initialized
                   configuration: filesystem=ext2 modified=2012-02-21 21:51:12 mount.fstype=ext2 mount.options=rw,relatime,errors=continue state=mounted
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@2:0.0.0,4
                   logical name: /dev/sda4
                   size: 153GiB
                   capacity: 153GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 7628MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      capacity: 46GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      logical name: /home
                      capacity: 99GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,user_xattr,acl,barrier=1,data=ordered state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: iHAS124   B
                vendor: ATAPI
                physical id: 0.1.0
                bus info: scsi@2:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: AL0S
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:500(size=32)
     *-scsi
          physical id: 1
          bus info: usb@1:2
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@4:0.0.1
             logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@4:0.0.2
             logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@4:0.0.3
             logical name: /dev/sde
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: 3e:a8:d3:67:9c:a8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.154 link=yes multicast=yes
kaipee@zoostorm-ubuntu:~$ 

```

---

### Post by Frogs Hair on 2012-02-21
Go to system settings > keyboard > shortcuts > system and enable the command prompt using Alt + F2.

Type lg into the command prompt and press enter . This displays Looking Glass and there you can check for errors that may shed some light on what may be happening. It reads like the shell is crashing and restarting . Press Esc to exit Looking Glass . 

[http://live.gnome.org/GnomeShell/CheatSheet](http://live.gnome.org/GnomeShell/CheatSheet)

---

### Post by fubofo on 2012-02-21
Thanks for the advice. It's a bit of a pain keeping it running over everything. I'll leave the machine on some day while at work to see if it catches anything.

One concern....will this also crash along with the desktop? If so will it log the errors so I can see once it restarts?

---

