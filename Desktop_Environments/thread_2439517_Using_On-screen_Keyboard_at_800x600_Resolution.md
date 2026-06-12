---
title: "Using On-screen Keyboard at 800x600 Resolution"
date: 2020-03-28
forum: Desktop Environments
---

### Post by slyads on 2020-03-28
I have a TFT display that is limited to 800x600 resolution. When I try and use the on-screen keyboard the bottom of it is cut off. Is there a way to set the position of the keyboard OR change the default size of the keyboard?  This is using 18.04.3.

---

### Post by Autodave on 2020-03-29
Will you give us some info on your equipment please?

---

### Post by slyads on 2020-03-29
So I did a little more experimentation last night and found that the issue happens with any display set to a resolution of 800x600.

[IMG]https://drive.google.com/open?id=1QVTsyxiX5QETJHQdpdC7hdtPvdvnnE5h[/IMG]
To answer your question though:

the display I am attempting to use is: [https://www.hopeindustrial.com/products/panel-mount-monitors/12-panel-mount-monitor/](https://www.hopeindustrial.com/products/panel-mount-monitors/12-panel-mount-monitor/)

```
System info:
    description: Desktop Computer
    product: B674 (788455)
    vendor: MicroElectronics
    version: 1.0
    serial: B674031950764
    width: 64 bits
    capabilities: smbios-3.1 dmi-3.1 smp vsyscall32
    configuration: boot=normal chassis=desktop family=PowerSpec sku=788455 uuid=7085C287-63BB-0000-0000-000000000000
  *-core
       description: Motherboard
       product: H310M-HDV/M.2
       vendor: ASRock
       physical id: 0
       serial: M80-B5015104059
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: P3.20D
          date: 01/07/2019
          size: 64KiB
          capacity: 15MiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: b
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: DIMM DDR4 Synchronous 2667 MHz (0.4 ns)
             product: GKE800UD102408-2666
             vendor: Numonyx (Intel)
             physical id: 0
             serial: 00000000
             slot: ChannelA-DIMM0
             size: 8GiB
             width: 64 bits
             clock: 2667MHz (0.4ns)
        *-bank:1
             description: DIMM DDR4 Synchronous 2667 MHz (0.4 ns)
             product: GKE800UD102408-2666
             vendor: Numonyx (Intel)
             physical id: 1
             serial: 00000000
             slot: ChannelB-DIMM0
             size: 8GiB
             width: 64 bits
             clock: 2667MHz (0.4ns)
     *-cache:0
          description: L1 cache
          physical id: 14
          slot: L1 Cache
          size: 384KiB
          capacity: 384KiB
          capabilities: synchronous internal write-back unified
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: 15
          slot: L2 Cache
          size: 1536KiB
          capacity: 1536KiB
          capabilities: synchronous internal write-back unified
          configuration: level=2
     *-cache:2
          description: L3 cache
          physical id: 16
          slot: L3 Cache
          size: 9MiB
          capacity: 9MiB
          capabilities: synchronous internal write-back unified
          configuration: level=3
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-8400 CPU @ 2.80GHz
          vendor: Intel Corp.
          physical id: 17
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-8400 CPU @ 2.80GHz
          serial: To Be Filled By O.E.M.
          slot: CPUSocket
          size: 1531MHz
          capacity: 4005MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp md_clear flush_l1d cpufreq
          configuration: cores=6 enabledcores=6 threads=6
     *-pci
          description: Host bridge
          product: 8th Gen Core Processor Host Bridge/DRAM Registers
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
          configuration: driver=skl_uncore
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16)
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:121 ioport:3000(size=4096) memory:a2000000-a30fffff ioport:90000000(size=301989888)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: GP107 [GeForce GTX 1050 Ti]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller cap_list
                configuration: latency=0
                resources: memory:a2000000-a2ffffff memory:90000000-9fffffff memory:a0000000-a1ffffff ioport:3000(size=128) memory:c0000-dffff
           *-multimedia
                description: Audio device
                product: GP107GL High Definition Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:a3080000-a3083fff
        *-generic
             description: Signal processing controller
             product: Cannon Lake PCH Thermal Controller
             vendor: Intel Corporation
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 10
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi cap_list
             configuration: driver=intel_pch_thermal latency=0
             resources: irq:16 memory:a333d000-a333dfff
        *-usb
             description: USB controller
             product: Cannon Lake PCH USB 3.1 xHCI Host Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 10
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:123 memory:a3320000-a332ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 5.3.0-42-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 5.03
                capabilities: usb-2.00
                configuration: driver=hub slots=16 speed=480Mbit/s
              *-usb:0
                   description: Keyboard
                   product: USB Keyboard
                   vendor: SIGMACHIP
                   physical id: 1
                   bus info: usb@1:1
                   version: 1.10
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=98mA speed=2Mbit/s
              *-usb:1
                   description: Mouse
                   product: Optical Mouse
                   vendor: Elan Microelectronics Corp.
                   physical id: 2
                   bus info: usb@1:2
                   version: 24.58
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
              *-usb:2
                   description: Bluetooth wireless interface
                   vendor: Intel Corp.
                   physical id: 4
                   bus info: usb@1:4
                   version: 0.01
                   capabilities: bluetooth usb-2.00
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 5.3.0-42-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 5.03
                capabilities: usb-3.10
                configuration: driver=hub slots=4 speed=10000Mbit/s
        *-memory UNCLAIMED
             description: RAM memory
             product: Cannon Lake PCH Shared SRAM
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 10
             width: 64 bits
             clock: 33MHz (30.3ns)
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:a3336000-a3337fff memory:a333c000-a333cfff
        *-communication
             description: Communication controller
             product: Cannon Lake PCH HECI Controller
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 10
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:126 memory:a333b000-a333bfff
        *-storage
             description: SATA controller
             product: Cannon Lake PCH SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: 10
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:124 memory:a3334000-a3335fff memory:a333a000-a333a0ff ioport:4050(size=8) ioport:4040(size=4) ioport:4020(size=32) memory:a3339000-a33397ff
        *-pci:1
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:122 memory:a3200000-a32fffff
           *-network DISABLED
                description: Wireless interface
                product: Dual Band Wireless-AC 3168NGW [Stone Peak]
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlp2s0
                version: 10
                serial: 18:56:80:33:0e:69
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=5.3.0-42-generic firmware=29.1044073957.0 latency=0 link=no multicast=yes wireless=IEEE 802.11
                resources: irq:127 memory:a3200000-a3201fff
        *-isa
             description: ISA bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: Cannon Lake PCH cAVS
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 10
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:128 memory:a3330000-a3333fff memory:a3100000-a31fffff
        *-serial:0 UNCLAIMED
             description: SMBus
             product: Cannon Lake PCH SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 10
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:a3338000-a33380ff ioport:efa0(size=32)
        *-serial:1 UNCLAIMED
             description: Serial bus controller
             product: Cannon Lake PCH SPI Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 10
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fe010000-fe010fff
        *-network
             description: Ethernet interface
             product: Ethernet Connection (7) I219-V
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             logical name: eno1
             version: 10
             serial: 70:85:c2:87:63:bb
             size: 1Gbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.5-4 ip=192.168.0.40 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
             resources: irq:125 memory:a3300000-a331ffff
     *-scsi:0
          physical id: 1
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD10EZEX-08W
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sda
             version: 1A02
             serial: WD-WCC6Y4KT029L
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=6117b31c
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sda1
                logical name: /data_store
                version: 1.0
                serial: 8b863b59-e212-4654-ac31-67ed57eb6490
                size: 931GiB
                capacity: 931GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                configuration: created=2019-10-06 21:40:09 filesystem=ext4 label=data lastmountpoint=/data_store modified=2020-03-24 03:54:09 mount.fstype=ext4 mount.options=rw,relatime mounted=2020-03-24 03:54:09 state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi2
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GH24NSC0
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: LY00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=open
     *-scsi:2
          physical id: 3
          logical name: scsi3
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC  WDS250G2B0B
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdb
             version: 00WD
             serial: 190714803681
             size: 232GiB (250GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=f435415a-59f1-428d-9d50-5569da953a09 logicalsectorsize=512 sectorsize=512
           *-volume:0
                description: Windows FAT volume
                vendor: mkfs.fat
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sdb1
                logical name: /boot/efi
                version: FAT32
                serial: d843-fc99
                size: 510MiB
                capacity: 511MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@3:0.0.0,2
                logical name: /dev/sdb2
                logical name: /
                version: 1.0
                serial: 2c964cac-9a60-46f8-8a2d-ef22144194dd
                size: 232GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                configuration: created=2019-10-06 20:06:22 filesystem=ext4 lastmountpoint=/ modified=2020-03-24 03:54:07 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro mounted=2020-03-24 03:54:08 state=mounted
```

---

### Post by webaake on 2020-03-29
Seems difficult to solve as I suspect the behaviuor is hardcoded into the Onboard keyboard. However, you could use wmctrl to move the window.

Onboard has the window name "Onboard" so it should be pretty easy to move with wmctrl. Open Onboard and check the window name with ```
wmctrl -l
```. Do wmctrl --help to check the possibilties. When you find the right setting you can attach the wmctrl command to a keyboard shortcut. 

PS You might have to install wmctrl. It's in the standard repos.

---

### Post by deadflowr on 2020-03-29
Open the Onboard preferences settings and try setting a different layout.
I see compact and full give a directional icon that if held can drag the keyboard up or down.

---

### Post by webaake on 2020-03-29
Oops! I've used Onboard for years and never seen that "directional icon" till now. Too easy! :lolflag:

---

### Post by slyads on 2020-03-30
I should have mentioned this in the title... I am not using onboard for this - I am using the Gnome built-in keyboard (accessible via settings -> universal access -> typing -> Screen Keyboard)

Is there a way to do this with the Gnome built-in keyboard?

---

