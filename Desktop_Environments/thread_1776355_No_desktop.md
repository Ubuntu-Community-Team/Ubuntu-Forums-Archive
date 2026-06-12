---
title: "No desktop?"
date: 2011-06-06
forum: Desktop Environments
---

### Post by linkdead1 on 2011-06-06
I hope this is in the right category....

Hi, I just installed Ubuntu 11.4 on a Dell Inspiron Laptop with an ATI Radeon HD video card.  When I try to log in, all I get is the background with no start menu or anything.  I can right click on the background and get basic options, but I cant connect to the net or anything.  Upon rebooting I chose Ubuntu Classic instead of the default desktop, and it works fine. I have also tried kubuntu and openSUSE, both have the same problem. I am thinking maybe graphics card driver?  

I am also having a problem with the computer not coming out of hibernation.

 Anyone have any ideas for me?

---

### Post by wildmanne39 on 2011-06-06
> **linkdead1 said:**
> I hope this is in the right category....

Hi, I just installed Ubuntu 11.4 on a Dell Inspiron Laptop with an ATI Radeon HD video card.  When I try to log in, all I get is the background with no start menu or anything.  I can right click on the background and get basic options, but I cant connect to the net or anything.  Upon rebooting I chose Ubuntu Classic instead of the default desktop, and it works fine. I have also tried kubuntu and openSUSE, both have the same problem. I am thinking maybe graphics card driver?  

I am also having a problem with the computer not coming out of hibernation.

 Anyone have any ideas for me?
Hi, that is probably it, log into classic and see if there is a driver for your card in the additional drivers. You can also run this command then post it here.
```
sudo lshw
```

---

### Post by Bucky Ball on 2011-06-06
But ... if the graphics driver is not running at boot why would logging in and out force it to run??? Sounds like the problem is with Unity not loading at boot, obviously, but Gnome is loading fine when you log out and change the desktop environment from Unity to Gnome.

I would begin to investigate why Unity is not loading at boot ... ;)

Welcome to the forums.

---

### Post by linkdead1 on 2011-06-06
Alright, so I upgraded my video driver, using fglrx, here is the readout of sudo lshw:

```

    description: Portable Computer
    version: A02
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6 smp-1.4 smp
    configuration: boot=normal chassis=portable cpus=2 sku=To be filled by O.E.M. uuid=44454C4C-3300-1037-8056-B4C04F394E31
  *-core
       description: Motherboard
       product: Inspiron M5030
       vendor: Winbond Electronics
       physical id: 0
       version: A02
       serial: .437V9N1.CN701660AL01QQ.
       slot: To Be Filled By O.E.M.
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
          capabilities: internal varies data
     *-memory
          description: System Memory
          physical id: 1d
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: KF073F-ELD
             vendor: AMD
             physical id: 0
             serial: 413EDDEC
             slot: DIMM_A
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: M471B2873FHS-CH9
             vendor: Samsung
             physical id: 1
             serial: 8027D29C
             slot: DIMM_B
             size: 1GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: SODIMM [empty]
             physical id: 2
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A02
          date: 08/05/2010
          size: 64KiB
          capacity: 1984KiB
          capabilities: mca pci upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) II P340 Dual-Core Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: 15.6.3
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 2200MHz
          capacity: 2200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a 3dnowprefetch osvw ibs skinit wdt nodeid_msr npt lbrv svm_lock nrip_save cpufreq
          configuration: cores=2 enabledcores=2
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 15.6.3
          size: 800MHz
          capacity: 800MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci:0
          description: Host bridge
          product: RS880 Host Bridge
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=32
        *-pci:0
             description: PCI bridge
             product: Dell
             vendor: Winbond Electronics
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:e000(size=4096) memory:ff300000-ff4fffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: M880G [Mobility Radeon HD 4200]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:11 memory:d0000000-dfffffff ioport:e000(size=256) memory:ff400000-ff40ffff memory:ff300000-ff3fffff
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 0)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 memory:ff600000-ff6fffff
           *-network
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: wlan0
                version: 01
                serial: 00:1b:b1:5d:8b:47
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A ip=192.168.1.102 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:16 memory:ff600000-ff60ffff
        *-pci:2
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 1)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:d000(size=4096) memory:ff500000-ff5fffff
           *-network
                description: Ethernet interface
                product: AR8152 v2.0 Fast Ethernet
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth0
                version: c1
                serial: f0:4d:a2:a4:2c:74
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                resources: irq:43 memory:ff500000-ff53ffff ioport:d000(size=128)
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             logical name: scsi1
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=32
             resources: irq:42 ioport:f090(size=8) ioport:f080(size=4) ioport:f070(size=8) ioport:f060(size=4) ioport:f050(size=16) memory:ff709000-ff7093ff
           *-disk
                description: ATA Disk
                product: WDC WD3200BEVT-7
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WXD1A8070528
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0008da2e
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 51114c0d-aaae-4c1d-904b-9e3ab41d2583
                   size: 295GiB
                   capacity: 295GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-06-05 22:19:30 filesystem=ext4 lastmountpoint=/ modified=2011-06-05 22:33:29 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,commit=600,barrier=1,data=ordered mounted=2011-06-06 17:34:28 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2811MiB
                   capacity: 2811MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2811MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVD+-RW DS-8A5SH
                vendor: PLDS
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: XD12
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:ff708000-ff708fff
        *-usb:1
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:ff707000-ff7070ff
        *-usb:2
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:ff706000-ff706fff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 42
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 40
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=32
             resources: irq:16 memory:ff700000-ff703fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master vga_palette
        *-usb:3
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:ff705000-ff705fff
        *-usb:4
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 16.2
             bus info: pci@0000:00:16.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:ff704000-ff7040ff
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
          physical id: 2
          bus info: usb@2:1
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
  *-battery
       description: Lithium Ion Battery
       product: DELL 4YRJH09
       vendor: Sanyo
       physical id: 1
       serial: 981
       slot: Sys. Battery Bay
       capacity: 45000mWh
       configuration: voltage=10.8V

```

Logged into regular Ubuntu and got the same thing, just the background.  It had saved my settings from Ubuntu classic and connected to the internet.  I can create folders and launchers and all that by right clicking the background.  I did a search for how to get the task bar back and it told me to do Alt+f2 and type in a command.  I did Alt+F2 but I didnt get the run application box.

---

### Post by wildmanne39 on 2011-06-06
> **linkdead1 said:**
> Alright, so I upgraded my video driver, using fglrx, here is the readout of sudo lshw:

```

    description: Portable Computer
    version: A02
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6 smp-1.4 smp
    configuration: boot=normal chassis=portable cpus=2 sku=To be filled by O.E.M. uuid=44454C4C-3300-1037-8056-B4C04F394E31
  *-core
       description: Motherboard
       product: Inspiron M5030
       vendor: Winbond Electronics
       physical id: 0
       version: A02
       serial: .437V9N1.CN701660AL01QQ.
       slot: To Be Filled By O.E.M.
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
          capabilities: internal varies data
     *-memory
          description: System Memory
          physical id: 1d
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: KF073F-ELD
             vendor: AMD
             physical id: 0
             serial: 413EDDEC
             slot: DIMM_A
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: M471B2873FHS-CH9
             vendor: Samsung
             physical id: 1
             serial: 8027D29C
             slot: DIMM_B
             size: 1GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: SODIMM [empty]
             physical id: 2
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A02
          date: 08/05/2010
          size: 64KiB
          capacity: 1984KiB
          capabilities: mca pci upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) II P340 Dual-Core Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: 15.6.3
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 2200MHz
          capacity: 2200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a 3dnowprefetch osvw ibs skinit wdt nodeid_msr npt lbrv svm_lock nrip_save cpufreq
          configuration: cores=2 enabledcores=2
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 15.6.3
          size: 800MHz
          capacity: 800MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci:0
          description: Host bridge
          product: RS880 Host Bridge
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=32
        *-pci:0
             description: PCI bridge
             product: Dell
             vendor: Winbond Electronics
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:e000(size=4096) memory:ff300000-ff4fffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: M880G [Mobility Radeon HD 4200]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:11 memory:d0000000-dfffffff ioport:e000(size=256) memory:ff400000-ff40ffff memory:ff300000-ff3fffff
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 0)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 memory:ff600000-ff6fffff
           *-network
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: wlan0
                version: 01
                serial: 00:1b:b1:5d:8b:47
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A ip=192.168.1.102 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:16 memory:ff600000-ff60ffff
        *-pci:2
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 1)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:d000(size=4096) memory:ff500000-ff5fffff
           *-network
                description: Ethernet interface
                product: AR8152 v2.0 Fast Ethernet
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth0
                version: c1
                serial: f0:4d:a2:a4:2c:74
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                resources: irq:43 memory:ff500000-ff53ffff ioport:d000(size=128)
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             logical name: scsi1
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=32
             resources: irq:42 ioport:f090(size=8) ioport:f080(size=4) ioport:f070(size=8) ioport:f060(size=4) ioport:f050(size=16) memory:ff709000-ff7093ff
           *-disk
                description: ATA Disk
                product: WDC WD3200BEVT-7
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WXD1A8070528
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0008da2e
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 51114c0d-aaae-4c1d-904b-9e3ab41d2583
                   size: 295GiB
                   capacity: 295GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-06-05 22:19:30 filesystem=ext4 lastmountpoint=/ modified=2011-06-05 22:33:29 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,commit=600,barrier=1,data=ordered mounted=2011-06-06 17:34:28 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2811MiB
                   capacity: 2811MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2811MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVD+-RW DS-8A5SH
                vendor: PLDS
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: XD12
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:ff708000-ff708fff
        *-usb:1
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:ff707000-ff7070ff
        *-usb:2
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:ff706000-ff706fff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 42
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 40
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=32
             resources: irq:16 memory:ff700000-ff703fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master vga_palette
        *-usb:3
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:ff705000-ff705fff
        *-usb:4
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 16.2
             bus info: pci@0000:00:16.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:ff704000-ff7040ff
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
          physical id: 2
          bus info: usb@2:1
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
  *-battery
       description: Lithium Ion Battery
       product: DELL 4YRJH09
       vendor: Sanyo
       physical id: 1
       serial: 981
       slot: Sys. Battery Bay
       capacity: 45000mWh
       configuration: voltage=10.8V

```

Logged into regular Ubuntu and got the same thing, just the background.  It had saved my settings from Ubuntu classic and connected to the internet.  I can create folders and launchers and all that by right clicking the background.  I did a search for how to get the task bar back and it told me to do Alt+f2 and type in a command.  I did Alt+F2 but I didnt get the run application box.
Hi, run this command in a terminal.
```
/usr/lib/nux/unity_support_test -p
``` please post the results here.

---

### Post by linkdead1 on 2011-06-07
```

OpenGL vendor string:   ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4200 Series
OpenGL version string:  3.3.10665 Compatibility Profile Context

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes

```

Thats the results, looks like everything should be ok...I think.

---

### Post by wildmanne39 on 2011-06-07
> **linkdead1 said:**
> ```

OpenGL vendor string:   ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4200 Series
OpenGL version string:  3.3.10665 Compatibility Profile Context

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes

```

Thats the results, looks like everything should be ok...I think.
Hi, that is good, I suspect you are missing the unity package this guide will walk you through how to fix the problem.
[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

---

