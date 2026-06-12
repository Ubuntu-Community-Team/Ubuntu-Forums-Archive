---
title: "Crashes?"
date: 2012-04-30
forum: Desktop Environments
---

### Post by Theredbaron1834 on 2012-04-30
I have been on Lubuntu for the past 3 releases, but I thought I would try KDE for a change. I like it a bit, but I have one problem. A couple times a day something crashes. Knet something is the main culprit, but not the only one. 

I have been on Ubuntu of one for or another since 9.04, with no crashes ever. So I am quite confused by this.
sudo lshw
```

[sudo] password for theredbaron: 
theredbaron-desktop       
    description: Desktop Computer
    product: To Be Filled By O.E.M. (To Be Filled By O.E.M.)
    vendor: To Be Filled By O.E.M.
    version: To Be Filled By O.E.M.
    serial: To Be Filled By O.E.M.
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: M3A770DE
       vendor: ASRock
       physical id: 0
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: P1.80
          date: 08/25/2011
          size: 64KiB
          capacity: 960KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) II X2 240 Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: AMD Athlon(tm) II X2 240 Processor
          serial: To Be Filled By O.E.M.
          slot: CPUSocket
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save cpufreq
          configuration: cores=2 enabledcores=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 12
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM Synchronous 400 MHz (2.5 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM Synchronous 400 MHz (2.5 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 2GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:2
             description: [empty]
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
        *-bank:3
             description: [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-pci:0
          description: Host bridge
          product: RX780/RX790 Chipset Host Bridge
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 64 bits
          clock: 66MHz
          resources: memory:0-1fffffff
        *-pci:0
             description: PCI bridge
             product: RD790 PCI to PCI bridge (external gfx0 port A)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:e000(size=4096) memory:feb00000-febfffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Juniper [Radeon HD 5700 Series]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:45 memory:d0000000-dfffffff memory:febe0000-febfffff ioport:e000(size=256) memory:febc0000-febdffff
           *-multimedia
                description: Audio device
                product: Juniper HDMI Audio [Radeon HD 5700 Series]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:44 memory:febbc000-febbffff
        *-pci:1
             description: PCI bridge
             product: RD790 PCI to PCI bridge (PCI express gpp port F)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:d000(size=4096) memory:fea00000-feafffff ioport:cff00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: 03
                serial: 00:25:22:46:fa:20
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-1.fw ip=192.168.1.90 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:43 ioport:d800(size=256) memory:cffff000-cfffffff memory:cfff8000-cfffbfff memory:feae0000-feafffff
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm msi ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=32
             resources: irq:42 ioport:c000(size=8) ioport:b000(size=4) ioport:a000(size=8) ioport:9000(size=4) ioport:8000(size=16) memory:fe9ff800-fe9ffbff
           *-disk
                description: ATA Disk
                product: ST9160827AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 3.AA
                serial: 5RF1P8SN
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=c87d8fbb
              *-volume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /media/042124c3-a88b-4daa-885a-7ebe0f856c38
                   version: 1.0
                   serial: 042124c3-a88b-4daa-885a-7ebe0f856c38
                   size: 149GiB
                   capacity: 149GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-01-29 21:42:31 filesystem=ext4 lastmountpoint=/media/042124c3-a88b-4daa-885a-7ebe0f856c38 modified=2012-04-30 00:09:13 mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,user_xattr,acl,barrier=1,data=ordered mounted=2012-04-30 00:09:13 state=mounted
        *-usb:0
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:16 memory:fe9fe000-fe9fefff
        *-usb:1
             description: USB controller
             product: SB7x0 USB OHCI1 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:16 memory:fe9fd000-fe9fdfff
        *-usb:2
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:fe9ff000-fe9ff0ff
        *-usb:3
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:fe9fc000-fe9fcfff
        *-usb:4
             description: USB controller
             product: SB7x0 USB OHCI1 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:fe9fb000-fe9fbfff
        *-usb:5
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:19 memory:fe9fa800-fe9fa8ff
        *-serial UNCLAIMED
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3c
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: SB7x0/SB8x0/SB9x0 IDE Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list emulated
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
           *-disk:0
                description: ATA Disk
                product: HDS728080PLAT20
                physical id: 0.0.0
                bus info: scsi@5:0.0.0
                logical name: /dev/sdb
                version: PF2O
                serial: PFD211S4RXYJTN
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000b145f
              *-volume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@5:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /media/4ca65388-8064-4293-aaea-b55b9ff68971
                   version: 1.0
                   serial: 4ca65388-8064-4293-aaea-b55b9ff68971
                   size: 74GiB
                   capacity: 74GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-01-30 09:50:45 filesystem=ext4 lastmountpoint=/media/4ca65388-8064-4293-aaea-b55b9ff68971 modified=2012-04-30 00:09:13 mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,user_xattr,acl,barrier=1,data=ordered mounted=2012-04-30 00:09:13 state=mounted
           *-disk:1
                description: ATA Disk
                product: ST340015A
                vendor: Seagate
                physical id: 0.1.0
                bus info: scsi@5:0.1.0
                logical name: /dev/sdc
                version: 3.15
                serial: 5LAJ1KBS
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00001055
              *-volume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@5:0.1.0,1
                   logical name: /dev/sdc1
                   logical name: /
                   version: 1.0
                   serial: bbf7bd89-a2d9-4874-889e-111dbb0d34f1
                   size: 37GiB
                   capacity: 37GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-04-26 18:55:34 filesystem=ext4 lastmountpoint=/ modified=2012-04-27 22:44:58 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2012-04-30 00:09:07 state=mounted
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:16 memory:fe9f4000-fe9f7fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
        *-usb:6
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:fe9f9000-fe9f9fff
     *-pci:1
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: 1
          bus info: usb@2:1
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdd

```uname -a
```
Linux theredbaron-desktop 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

So is this a known problem, or should I try a reinstall? Do you see something that would cause a problem?

---

### Post by whatthefunk on 2012-04-30
Ive never had Kubuntu crash on me.  It would help if you could post logs from the time of the crash.

---

### Post by Theredbaron1834 on 2012-04-30
Honestly, I didn't even think about it when it happened. Just sitting back watching a video now, and thought I would ask if it has happened before.  I guess it isn't. I'll remember next time. :)

---

### Post by marl30 on 2012-04-30
It's always stable and reliable for me. No crashes here neither. No wonder after every Ubuntu release, since the last three releases, I always find myself back using Kubuntu.

---

### Post by Theredbaron1834 on 2012-05-03
Well, I havn't had a crash since my last update. So whatever it was is gone now.

Side note: I like it quite alot, except for a few "bugs" HDMI audio breaks after I use my bluetooth headset, and everything is just a bit slow. I guess it's really that LXDE is a bit fast, it was the one I left. Doubt I will stick with Kubuntu myself. But it is very nice.

---

