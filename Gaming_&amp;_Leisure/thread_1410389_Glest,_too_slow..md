---
title: "Glest, too slow."
date: 2010-02-18
forum: Gaming &amp; Leisure
---

### Post by alket on 2010-02-18
I've just installed Glest from USS but it runs slow, how to fix it ?

---

### Post by alket on 2010-02-18
Anyone ?

---

### Post by Chesnut on 2010-02-19
Got proper video card drivers?

---

### Post by alket on 2010-02-19
lshw output
```
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: 15.15.2
          slot: Socket 939
          size: 1GHz
          capacity: 3GHz
          width: 64 bits
          clock: 201MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up pni lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: b
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: d
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back
     *-cpu:1 DISABLED
          description: CPU
          vendor: Unknown
          physical id: 5
          bus info: cpu@1
          version: 15.15.2
          slot: Socket 939
          size: 2211MHz
          capacity: 3GHz
          clock: 201MHz
        *-cache:0
             description: L1 cache
             physical id: c
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: e
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back
     *-memory:0
          description: System Memory
          physical id: 1e
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: DIMM
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 512MiB
             width: 64 bits
        *-bank:2
             description: DIMM
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             size: 512MiB
             width: 64 bits
        *-bank:3
             description: DIMM
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
             size: 512MiB
             width: 64 bits
     *-memory:1 UNCLAIMED
          description: Memory controller
          product: CK804 Memory Controller
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:00.0
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: CK804 ISA Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: CK804 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3
          resources: irq:10 ioport:fc00(size=32) ioport:4c00(size=64) ioport:4c40(size=64)
     *-usb:0
          description: USB Controller
          product: CK804 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:20 memory:fe02f000-fe02ffff
     *-usb:1
          description: USB Controller
          product: CK804 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:21 memory:feb00000-feb000ff
     *-multimedia
          description: Multimedia audio controller
          product: CK804 AC'97 Audio Controller
          vendor: nVidia Corporation
          physical id: f
          bus info: pci@0000:00:04.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2
          resources: irq:22 ioport:f000(size=256) ioport:ec00(size=256) memory:fe02d000-fe02dfff
     *-ide:0
          description: IDE interface
          product: CK804 IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          logical name: scsi4
          version: f2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:e000(size=16)
        *-cdrom
             description: DVD writer
             product: DVDRRW GWA-4164B
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: 1.03
             serial: [HL-DT-STDVDRRW GWA-4164B1.0305/05/23
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
        *-disk
             description: ATA Disk
             product: ST320011A
             vendor: Seagate
             physical id: 0.1.0
             bus info: scsi@4:0.1.0
             logical name: /dev/sdb
             version: 3.21
             serial: 3HT548C3
             size: 18GiB (20GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=00370037
           *-volume
                description: Windows FAT volume
                vendor: mkdosfs
                physical id: 1
                bus info: scsi@4:0.1.0,1
                logical name: /dev/sdb1
                version: FAT32
                serial: e02d-c516
                size: 18GiB
                capacity: 18GiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat
     *-ide:1
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: scsi0
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:cc00(size=16) memory:fe02b000-fe02bfff
        *-disk
             description: ATA Disk
             product: WDC WD2500JS-55N
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 10.0
             serial: WD-WMANK1446941
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=c574c574
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 5f9411f7-c088-43ca-b6d7-a4bb4a82f4e7
                size: 227GiB
                capacity: 227GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2010-02-18 18:00:26 filesystem=ext4 lastmountpoint=/{&#65533;&#65533;fs&#65533;`(&#65533;&#65533;&#65533;as&#65533;&#65533;^&#65533;&#65533;&#65533;]&#65533;`&#65533;&#65533;&#65533;`&#65533;&#65533;&#65533;fs&#65533;&#65533;^&#65533;&#65533;^&#65533;&#65533;U`&#65533;fs&#65533;`&#65533;%&#65533; modified=2010-02-19 14:08:35 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-02-19 14:08:36 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 5898MiB
                capacity: 5898MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 5898MiB
                   capabilities: nofs
     *-ide:2
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:22 ioport:9e0(size=8) ioport:be0(size=4) ioport:960(size=8) ioport:b60(size=4) ioport:b800(size=16) memory:fe02a000-fe02afff
     *-pci:0
          description: PCI bridge
          product: CK804 PCI Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci bus_master
          resources: ioport:a000(size=4096) memory:fde00000-fdefffff memory:fdf00000-fdffffff(prefetchable)
        *-firewire
             description: FireWire (IEEE 1394)
             product: VT6306 Fire II IEEE 1394 OHCI Link Layer Controller
             vendor: VIA Technologies, Inc.
             physical id: c
             bus info: pci@0000:01:0c.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci1394 latency=32
             resources: irq:19 memory:fdeff000-fdeff7ff ioport:ac00(size=128)
     *-bridge
          description: Ethernet interface
          product: CK804 Ethernet Controller
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth0
          version: a3
          serial: 00:13:d3:ad:46:6a
          size: 10000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=half latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=10MB/s
          resources: irq:23 memory:fe029000-fe029fff ioport:b400(size=8)
     *-pci:1
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
          resources: irq:24 ioport:9000(size=4096) memory:fdd00000-fddfffff ioport:fdc00000(size=1048576)
     *-pci:2
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
          resources: irq:25 ioport:8000(size=4096) memory:fdb00000-fdbfffff ioport:fda00000(size=1048576)
     *-pci:3
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
          resources: irq:26 ioport:7000(size=4096) memory:fd900000-fd9fffff ioport:fd800000(size=1048576)
     *-pci:4
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
          resources: irq:27 ioport:6000(size=4096) memory:fd700000-fd7fffff ioport:d0000000(size=268435456)
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: RV410 [Radeon X700]
             vendor: ATI Technologies Inc
             physical id: 0
             bus info: pci@0000:05:00.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list
             configuration: latency=0
             resources: memory:d0000000-dfffffff(prefetchable) memory:fd7f0000-fd7fffff ioport:6c00(size=256) memory:fd700000-fd71ffff(prefetchable)
        *-display:1 UNCLAIMED
             description: Display controller
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 0.1
             bus info: pci@0000:05:00.1
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress cap_list
             configuration: latency=0
             resources: memory:fd7e0000-fd7effff
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi
          physical id: 10
          bus info: usb@1:9
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             product: STORAGE DEVICE
             vendor: Generic
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdc
             version: 9144
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdc
        *-disk:1
             description: SCSI Disk
             product: STORAGE DEVICE
             vendor: Generic
             physical id: 0.0.1
             bus info: scsi@6:0.0.1
             logical name: /dev/sdd
             version: 9144
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdd
        *-disk:2
             description: SCSI Disk
             product: STORAGE DEVICE
             vendor: Generic
             physical id: 0.0.2
             bus info: scsi@6:0.0.2
             logical name: /dev/sde
             version: 9144
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sde
        *-disk:3
             description: SCSI Disk
             product: STORAGE DEVICE
             vendor: Generic
             physical id: 0.0.3
             bus info: scsi@6:0.0.3
             logical name: /dev/sdf
             version: 9144
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdf
        *-disk:4
             description: SCSI Disk
             product: STORAGE DEVICE
             vendor: Generic
             physical id: 0.0.4
             bus info: scsi@6:0.0.4
             logical name: /dev/sdg
             version: 9144
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdg
```

lspci output
> 00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
05:00.0 VGA compatible controller: ATI Technologies Inc RV410 [Radeon X700]
05:00.1 Display controller: ATI Technologies Inc Device 5e6f


---

### Post by ultifd on 2010-02-19
You will probably have a better chance of fixing your problem if you post in the glest forums. ([http://glest.org/glest_board/](http://glest.org/glest_board/))
Good luck.

---

### Post by handy on 2010-02-20
Are you running the Catalyst drivers or the open-source ones?

If I try to play Glest with the open source ones it is too slow to be playable.  If I use the Catalyst drivers it plays perfectly.

---

