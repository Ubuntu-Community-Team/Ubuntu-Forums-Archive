---
title: "Screen flickers then goes black in 11.04 Natty Narwhal"
date: 2012-03-05
forum: Desktop Environments
---

### Post by endian675 on 2012-03-05
Hi, my 11.04 install has been solid since I installed it.  Something strange has started happening in the last day or so.  For a few seconds the screen flickers slightly, going a little darker, then a little brighter, then finally another second or so later it goes completely black.  The monitor is still receiving a signal (its LED changes from blue to orange when it's not) and the machine is still running.  If I do Ctrl-Alt-Del and hit enter, the machine will usually shutdown - in fact, sometimes the screen comes back and I can see the output of the shutdown sequence, so the machine hasn't crashed.  

I have seen mention of flickering/black screens elsewhere and saw that someone was asked for the output of the commands lspci |grep VGA and lshw, so here they are in case they're useful:

```
01:00.0 VGA compatible controller: nVidia Corporation GF110 [Geforce GTX 570] (rev a1)
02:00.0 VGA compatible controller: nVidia Corporation GF104 [GeForce GTX 460] (rev a1)
```

lshw: 
```

gpu3
    description: Desktop Computer
    product: System Product Name (To be filled by O.E.M.)
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop family=To be filled by O.E.M. sku=To be filled by O.E.M. uuid=40FFD333-8957-E011-AE97-F46D0411A7A7
  *-core
       description: Motherboard
       product: Maximus IV Extreme
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev 1.xx
       serial: 109188030000096
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1204
          date: 03/02/2011
          size: 64KiB
          capacity: 4032KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz
          serial: To Be Filled By O.E.M.
          slot: LGA1155
          size: 3425MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt aes xsave avx lahf_lm ida arat epb xsaveopt pln pts tpr_shadow vnmi flexpriority ept vpid
          configuration: cores=4 enabledcores=1 threads=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: internal varies unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 8MiB
             capacity: 8MiB
             capabilities: internal unified
     *-memory
          description: System Memory
          physical id: 24
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: DIMM Synchronous [empty]
             product: Array1_PartNumber0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             width: 64 bits
        *-bank:1
             description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: CMZ8GX3M2A1600C9
             vendor: Corsair
             physical id: 1
             serial: 0000000
             slot: DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:2
             description: DIMM Synchronous [empty]
             product: Array1_PartNumber2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             width: 64 bits
        *-bank:3
             description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: CMZ8GX3M2A1600C9
             vendor: Corsair
             physical id: 3
             serial: 0000000
             slot: DIMM3
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 2nd Generation Core Processor Family PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:e000(size=4096) memory:f9000000-fa0fffff ioport:d0000000(size=167772160)
           *-display
                description: VGA compatible controller
                product: GF110 [Geforce GTX 570]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:f9000000-f9ffffff memory:d0000000-d7ffffff memory:d8000000-d9ffffff ioport:e000(size=128) memory:fa000000-fa07ffff
           *-multimedia
                description: Audio device
                product: GF110 High Definition Audio Controller
                vendor: nVidia Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:17 memory:fa080000-fa083fff
        *-pci:1
             description: PCI bridge
             product: 2nd Generation Core Processor Family PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:d000(size=4096) memory:f6000000-f80fffff ioport:c0000000(size=201326592)
           *-display
                description: VGA compatible controller
                product: GF104 [GeForce GTX 460]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:17 memory:f6000000-f7ffffff memory:c0000000-c7ffffff memory:c8000000-cbffffff ioport:d000(size=128) memory:f8000000-f807ffff
           *-multimedia
                description: Audio device
                product: GF104 High Definition Audio Controller
                vendor: nVidia Corporation
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:18 memory:f8080000-f8083fff
        *-communication UNCLAIMED
             description: Communication controller
             product: 6 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:f8129000-f812900f
        *-network
             description: Ethernet interface
             product: 82579V Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 05
             serial: f4:6d:04:11:a7:a7
             size: 1Gbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.2.20-k2 duplex=full firmware=0.13-4 ip=192.168.4.25 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
             resources: irq:51 memory:f8100000-f811ffff memory:f8128000-f8128fff ioport:f040(size=32)
        *-usb:0
             description: USB Controller
             product: 6 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f8127000-f81273ff
        *-multimedia
             description: Audio device
             product: 6 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:54 memory:f8120000-f8123fff
        *-pci:2
             description: PCI bridge
             product: 6 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 memory:fa500000-fa5fffff
           *-pci
                description: PCI bridge
                product: PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch
                vendor: PLX Technology, Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: ba
                width: 32 bits
                clock: 33MHz
                capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                configuration: driver=pcieport
                resources: irq:46 memory:fa500000-fa51ffff
              *-pci:0
                   description: PCI bridge
                   product: PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch
                   vendor: PLX Technology, Inc.
                   physical id: 0
                   bus info: pci@0000:04:00.0
                   version: ba
                   width: 64 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: iomemory:1f10-1f0f irq:47
              *-pci:1
                   description: PCI bridge
                   product: PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch
                   vendor: PLX Technology, Inc.
                   physical id: 5
                   bus info: pci@0000:04:05.0
                   version: ba
                   width: 64 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: iomemory:1f10-1f0f irq:48
              *-pci:2
                   description: PCI bridge
                   product: PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch
                   vendor: PLX Technology, Inc.
                   physical id: 7
                   bus info: pci@0000:04:07.0
                   version: ba
                   width: 64 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: iomemory:1f10-1f0f irq:49
              *-pci:3
                   description: PCI bridge
                   product: PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch
                   vendor: PLX Technology, Inc.
                   physical id: 9
                   bus info: pci@0000:04:09.0
                   version: ba
                   width: 64 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: iomemory:1f10-1f0f irq:50
        *-pci:3
             description: PCI bridge
             product: 6 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 memory:fa400000-fa4fffff
           *-usb
                description: USB Controller
                product: uPD720200 USB 3.0 Host Controller
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:09:00.0
                version: 04
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:17 memory:fa400000-fa401fff
        *-pci:4
             description: PCI bridge
             product: 6 Series Chipset Family PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:44 memory:fa300000-fa3fffff
           *-usb
                description: USB Controller
                product: uPD720200 USB 3.0 Host Controller
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:0a:00.0
                version: 04
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:18 memory:fa300000-fa301fff
        *-pci:5
             description: PCI bridge
             product: 6 Series Chipset Family PCI Express Root Port 7
             vendor: Intel Corporation
             physical id: 1c.6
             bus info: pci@0000:00:1c.6
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:45 ioport:c000(size=4096) memory:fa200000-fa2fffff
           *-network
                description: Ethernet interface
                product: 82583V Gigabit Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0b:00.0
                logical name: eth1
                version: 00
                serial: f4:6d:04:11:a6:07
                capacity: 1Gbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.2.20-k2 firmware=1.10-0 latency=0 link=no multicast=yes port=twisted pair
                resources: irq:53 memory:fa200000-fa21ffff ioport:c000(size=32) memory:fa220000-fa223fff
        *-usb:1
             description: USB Controller
             product: 6 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f8126000-f81263ff
        *-isa
             description: ISA bridge
             product: P67 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 6 Series Chipset Family 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             logical name: scsi5
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:52 ioport:f090(size=8) ioport:f080(size=4) ioport:f070(size=8) ioport:f060(size=4) ioport:f020(size=32) memory:f8125000-f81257ff
           *-disk:0
                description: ATA Disk
                product: INTEL SSDSC2MH12
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: PPG2
                serial: LNEL109300XG120CGN
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0009ea6d
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: a038d3c1-f50c-4976-acf5-4f8fc9a3d489
                   size: 103GiB
                   capacity: 103GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-12-04 11:27:24 filesystem=ext4 lastmountpoint=/ modified=2012-02-04 10:39:12 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2012-03-05 20:33:54 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 8167MiB
                   capacity: 8167MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 8167MiB
                      capabilities: nofs
           *-disk:1
                description: ATA Disk
                product: WDC WD1002FAEX-0
                vendor: Western Digital
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sdb
                version: 05.0
                serial: WD-WCAW31220177
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=dc1c87ea
              *-volume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sdb1
                   version: 1.0
                   serial: f08a9412-ed0e-4164-94c9-9f4a87d3c859
                   size: 931GiB
                   capacity: 931GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2011-05-29 18:29:11 filesystem=ext4 label=STORAGE lastmountpoint=/media/STORAGE modified=2012-02-04 10:30:33 mounted=2012-02-02 16:51:33 state=clean
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RW  DVR-219L
                vendor: PIONEER
                physical id: 0.0.0
                bus info: scsi@5:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.01
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f8124000-f81240ff ioport:1180(size=32)
  *-power:0 UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 1
       version: To Be Filled By O.E.M.
       serial: To Be Filled By O.E.M.
       capacity: 32768mWh
  *-power:1 UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 2
       version: To Be Filled By O.E.M.
       serial: To Be Filled By O.E.M.
       capacity: 32768mWh
```

---

### Post by endian675 on 2012-03-06
It seems this is most likely a hardware issue, as I experienced the same after I switched back to my Windows PC on the same display and  cable.  I've changed the cable and have just had the issue again (seems it can be revived by taking the cable out and re-inserting it), so presumably the monitor is playing up.

---

