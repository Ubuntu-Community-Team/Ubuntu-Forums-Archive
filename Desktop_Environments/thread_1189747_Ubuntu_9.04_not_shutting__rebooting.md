---
title: "Ubuntu 9.04 not shutting / rebooting"
date: 2009-06-17
forum: Desktop Environments
---

### Post by BharatBSahni on 2009-06-17
I have downloaded Ubuntu 9.04 (64bit), on a system which is running windows xp sp3.

Ubuntu 9.04 does not shut or reboot after giving the shut down command.

It has to be shut down forcibly by swithching off the power Button.

Please help.

Bharat

---

### Post by Waappu on 2009-06-17
Hi

What motherboard do you have ?

Probably you need set some kernel option. e.g.

---

### Post by BharatBSahni on 2009-06-17
> **Waappu said:**
> Hi

What motherboard do you have ?

Probably you need set some kernel option. e.g.

Dear/s,

Thanks,

As desired I give the following information;

The motherboard is Intel Desktop Board D101GGC

For further information this is to be informed, If this can help;

1. (Though it may not be pertinent) All the Previous versions were running successfully of Ubuntu/Kubuntu 64 bit, (from Ubuntu/Kubuntu 7.04 to Ubuntu/Kubuntu 8.04).

2. The present installation is made through downloading and burning the CD of Ubuntu 9.04 64 bit from the net.

3. Except shutting down / reboot problem all other functions / applications are working.

Bharat

---

### Post by ~sHyLoCk~ on 2009-06-18
You can't shutdown using:
```
sudo shutdown -hP now
```
?

---

### Post by metiosarius on 2009-06-18
There is an outstanding issue with some systems where you have to press random keys or move the mouse around in order to get the boot/shutdown process to continue. As far as I know, there is no solution at the moment other than pressing keys. Give it a try...

---

### Post by lisati on 2009-06-18
Another issue I'm aware of (not sure if it has been fixed yet) is that some systems hang on shutdown/restart if there is a wireless card active. I usually have my laptop hooked up via a wired connection and the wireless switched off, which seems to help avoid it hanging.

---

### Post by configt on 2009-07-02
Hello all.

I am having a similar issue with rebooting / shutting down in 9.04.  I had no problems with 8.10, but since I installed 9.04 from scratch (didn't upgrade 8.10) shutting down and rebooting has not worked properly.

In my case, choosing shutdown (or running from shell) causes a reboot instead of a shutdown.  Occasionally there will be many beeps from the PC speaker during the attempted shutdown.  In order to actually shutdown the computer, I have to hold down the power button before the OS boots again.  Every 3rd time or so, I cannot boot up without first booting into recovery mode because the PC speaker will just beep endlessly and bootup is halted or my screens go into power save mode.

Here are the specs of my system in case anyone is interested in solving this problem.

**OS:** Linux shamwow.port2002.com 2.6.28-13-generic #44-Ubuntu SMP Tue Jun 2 07:57:31 UTC 2009 i686 GNU/Linux

**Hardware:**
```

shamwow.port2002.com
    description: Computer
    product: Springdale-G
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal cpus=1 uuid=948D8AD9-4013-11D9-84F6-00E018874439
  *-core
       description: Motherboard
       product: D865PERL
       vendor: Intel Corporation
       physical id: 0
       version: AAC27646-213
       serial: BTRL44826916
       slot: Audio Mic In
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 0
          version: RL86510A.86A.0089.P21.0502132202 (02/13/2005)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int1
3floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int1
3floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acp
i usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.3.4
          serial: 0000-0F34-0000-0000-0000-0000
          slot: J2E1
          size: 3400MHz
          capacity: 3400MHz
          width: 32 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8
 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht t
m pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: None
             size: 16KiB
             capacity: 16KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: None
             size: 1MiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 39
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM DDR Synchronous 400 MHz (2.5 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 0
             serial: SerNum1
             slot: J5G1
             size: 512MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM DDR Synchronous 400 MHz (2.5 ns) [empty]
             product: PartNum2
             vendor: Manufacturer2
             physical id: 1
             serial: SerNum2
             slot: J5G2
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:2
             description: DIMM DDR Synchronous 400 MHz (2.5 ns)
             product: PartNum3
             vendor: Manufacturer3
             physical id: 2
             serial: SerNum3
             slot: J5H1
             size: 512MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:3
             description: DIMM DDR Synchronous 400 MHz (2.5 ns) [empty]
             product: PartNum4
             vendor: Manufacturer4
             physical id: 3
             serial: SerNum4
             slot: J5H2
             width: 64 bits
             clock: 400MHz (2.5ns)
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82865G/PE/P PCI to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-display:0 UNCLAIMED
                description: VGA compatible controller
                product: Radeon R350 [Radeon 9800 Pro]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-3.0 pm cap_list
                configuration: latency=0 mingnt=8
           *-display:1 UNCLAIMED
                description: Display controller
                product: Radeon R350 [Radeon 9800 Pro] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm cap_list
                configuration: latency=0 mingnt=8
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-pci
                description: PCI bridge
                product: PEX8112 x1 Lane PCI Express-to-PCI Bridge
                vendor: PLX Technology, Inc.
                physical id: 3
                bus info: pci@0000:02:03.0
                version: aa
                width: 32 bits
                clock: 66MHz
                capabilities: pci pm msi pciexpress bus_master cap_list
              *-display
                   description: VGA compatible controller
                   product: GeForce 8400 GS
                   vendor: nVidia Corporation
                   physical id: 0
                   bus info: pci@0000:03:00.0
                   version: a1
                   width: 64 bits
                   clock: 33MHz
                   capabilities: pm msi pciexpress bus_master cap_list
                   configuration: driver=nvidia latency=0 module=nvidia
           *-network:0
                description: Ethernet interface
                product: RTL8139 Ethernet
                vendor: D-Link System Inc
                physical id: 4
                bus info: pci@0000:02:04.0
                logical name: eth0
                version: 10
                serial: 00:0d:88:3b:bd:4c
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10
bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too d
riverversion=0.9.28 duplex=full ip=169.254.6.63 latency=32 link=yes maxlatency=6
4 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
           *-firewire
                description: FireWire (IEEE 1394)
                product: FW323
                vendor: Agere Systems
                physical id: 7
                bus info: pci@0000:02:07.0
                version: 61
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=24 mingnt=1
2 module=ohci1394
           *-network:1
                description: Ethernet interface
                product: 82562EZ 10/100 Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth1
                version: 01
                serial: 00:11:11:b3:4c:c0
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10
bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driv
erversion=3.5.23-k6-NAPI duplex=full firmware=N/A ip=192.168.0.11 latency=32 lin
k=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
           *-cdrom
                description: DVD reader
                product: 48MAX 244816AJ
                vendor: Memorex
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: KWH8
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
           *-disk
                description: ATA Disk
                product: MAXTOR STM350063
                vendor: Maxtor
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: 3.AA
                serial: 9QG1F0DS
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=19991b1c
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: c6b9db74-d314-2e48-91e2-cb815f4cc9f5
                   size: 465GiB
                   capacity: 465GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2007-10-21 17:24:36 f
ilesystem=ntfs label=BACKUPS state=clean
        *-ide:1
             description: IDE interface
             product: 82801EB (ICH5) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             logical name: scsi3
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
           *-disk:0
                description: ATA Disk
                product: ST3300622AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sdb
                version: 3.AA
                serial: 5NF28DYY
                size: 279GiB (300GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0b23abec
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /media/DISK3_VOL1
                   version: 3.1
                   serial: 1a654cd0-5796-d44b-96ab-9c72fcd92a40
                   size: 230GiB
                   capacity: 230GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2006-07-12 23:23:29 f
ilesystem=ntfs label=DISK3_VOL1 mount.fstype=fuseblk mount.options=rw,nosuid,nod
ev,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sdb2
                   size: 48GiB
                   capacity: 48GiB
                   capabilities: primary extended partitioned partitioned:extend
ed
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sdb5
                      logical name: /
                      capacity: 46GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime
,errors=remount-ro,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sdb6
                      capacity: 2086MiB
                      capabilities: nofs
           *-disk:1
                description: ATA Disk
                product: ST3300622AS
                vendor: Seagate
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/sdc
                version: 3.AA
                serial: 5NF25ZE1
                size: 279GiB (300GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=216b5230
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sdc1
                   version: 3.1
                   serial: 16b2f94c-e849-ee46-ad2c-1e98807b1110
                   size: 279GiB
                   capacity: 279GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2006-07-13 00:13:22 f
ilesystem=ntfs label=DISK4_VOL1 state=clean
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 4a:6b:25:27:a5:a5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A
 link=yes multicast=yes

```
**DMESG:**
```

[    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-13-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #44-Ubuntu SMP Tue Jun 2 07:57:31 UTC 2009 (Ubuntu 2.6.28-13.44-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fe30000 (usable)
[    0.000000]  BIOS-e820: 000000003fe30000 - 000000003fe3e6d5 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003ff10000 - 000000003ff30000 (reserved)
[    0.000000]  BIOS-e820: 000000003ff30000 - 000000003ff40000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ff40000 - 000000003fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fecf0000 - 00000000fecf1000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x3fe30 max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000092c00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003fe30000 (usable)
[    0.000000]  modified: 000000003fe30000 - 000000003fe3e6d5 (ACPI NVS)
[    0.000000]  modified: 000000003ff10000 - 000000003ff30000 (reserved)
[    0.000000]  modified: 000000003ff30000 - 000000003ff40000 (ACPI data)
[    0.000000]  modified: 000000003ff40000 - 000000003fff0000 (ACPI NVS)
[    0.000000]  modified: 000000003fff0000 - 0000000040000000 (reserved)
[    0.000000]  modified: 00000000fecf0000 - 00000000fecf1000 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378be000 - 37feffdd
[    0.000000] Allocated new RAMDISK: 0087b000 - 00facfdd
[    0.000000] Move RAMDISK from 00000000378be000 - 0000000037feffdc to 0087b000 - 00facfdc
[    0.000000] ACPI: RSDP 000F62C0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 3FF30000, 0034 (r1 INTEL  D865PERL 20050213 MSFT       97)
[    0.000000] ACPI: FACP 3FF30200, 0081 (r2 INTEL  D865PERL 20050213 MSFT       97)
[    0.000000] ACPI: DSDT 3FF30370, 4272 (r1 INTEL  D865PERL        6 MSFT  100000D)
[    0.000000] ACPI: FACS 3FF40000, 0040
[    0.000000] ACPI: APIC 3FF30300, 0068 (r1 INTEL  D865PERL 20050213 MSFT       97)
[    0.000000] ACPI: ASF! 3FF345F0, 0099 (r16 LEGEND I865PASF        1 MSFT  100000D)
[    0.000000] ACPI: WDDT 3FF34689, 0040 (r1 INTEL  OEMWDDT         1 MSFT  100000D)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 138MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008760ac]    TEXT DATA BSS ==> [0000100000 - 00008760ac]
[    0.000000]   #4 [0000877000 - 000087b000]    INIT_PG_TABLE ==> [0000877000 - 000087b000]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [000087b000 - 0000facfdd]      NEW RAMDISK ==> [000087b000 - 0000facfdd]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00ff780] 000ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x0003fe30
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000092
[    0.000000]     0: 0x00000100 -> 0x0003fe30
[    0.000000] On node 0 totalpages: 261557
[    0.000000] free_area_init_node: node 0, pgdat c06c9500, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3941 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 277 pages used for memmap
[    0.000000]   HighMem zone: 35101 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e6000
[    0.000000] PM: Registered nosave memory: 00000000000e6000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:becf0000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259512
[    0.000000] Kernel command line: root=UUID=d1506a14-1c93-456b-bcc9-3a89ddb43ac5 ro splash
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3391.870 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 5233600 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 1016692k/1046720k available (4110k kernel code, 29268k reserved, 2197k data, 532k init, 141512k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0731000 - 0xc07b6000   ( 532 kB)
[    0.004000]       .data : 0xc05039df - 0xc0728e60   (2197 kB)
[    0.004000]       .text : 0xc0100000 - 0xc05039df   (4110 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004010] Calibrating delay loop (skipped), value calculated using timer frequency.. 6783.74 BogoMIPS (lpj=13567480)
[    0.004257] Security Framework initialized
[    0.004373] SELinux:  Disabled at boot.
[    0.004502] AppArmor: AppArmor initialized
[    0.004623] Mount-cache hash table entries: 512
[    0.004874] Initializing cgroup subsys ns
[    0.004988] Initializing cgroup subsys cpuacct
[    0.005101] Initializing cgroup subsys memory
[    0.005217] Initializing cgroup subsys freezer
[    0.005344] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.005531] CPU: L2 cache: 1024K
[    0.005641] CPU: Physical Processor ID: 0
[    0.005752] CPU: Processor Core ID: 0
[    0.005864] using mwait in idle threads.
[    0.005984] Checking 'hlt' instruction... OK.
[    0.023086] ACPI: Core revision 20080926
[    0.025530] ACPI: Checking initramfs for custom DSDT
[    0.280360] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.320173] CPU0: Intel(R) Pentium(R) 4 CPU 3.40GHz stepping 04
[    0.324001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 6783.36 BogoMIPS (lpj=13566730)
[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.408272] CPU1: Intel(R) Pentium(R) 4 CPU 3.40GHz stepping 04
[    0.409246] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.412050] Brought up 2 CPUs
[    0.412161] Total of 2 processors activated (13567.10 BogoMIPS).
[    0.412321] CPU0 attaching sched-domain:
[    0.412325]  domain 0: span 0-1 level SIBLING
[    0.412328]   groups: 0 1
[    0.412335] CPU1 attaching sched-domain:
[    0.412337]  domain 0: span 0-1 level SIBLING
[    0.412339]   groups: 1 0
[    0.412413] net_namespace: 776 bytes
[    0.412413] Booting paravirtualized kernel on bare hardware
[    0.412595] Time:  9:59:12  Date: 07/02/09
[    0.412595] regulator: core version 0.5
[    0.412595] NET: Registered protocol family 16
[    0.412595] EISA bus registered
[    0.412658] ACPI: bus type pci registered
[    0.416558] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
[    0.416678] PCI: Using configuration type 1 for base access
[    0.417826] ACPI: EC: Look up EC in DSDT
[    0.425519] ACPI: Interpreter enabled
[    0.425634] ACPI: (supports S0 S1 S4 S5)
[    0.426050] ACPI: Using IOAPIC for interrupt routing
[    0.432937] ACPI: No dock devices found.
[    0.433061] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.433228] pci 0000:00:00.0: reg 10 32bit mmio: [0xc0000000-0xcfffffff]
[    0.433352] pci 0000:00:1d.0: reg 20 io port: [0xcc00-0xcc1f]
[    0.433402] pci 0000:00:1d.1: reg 20 io port: [0xd000-0xd01f]
[    0.433452] pci 0000:00:1d.2: reg 20 io port: [0xd400-0xd41f]
[    0.433502] pci 0000:00:1d.3: reg 20 io port: [0xd800-0xd81f]
[    0.433561] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfd300000-0xfd3003ff]
[    0.433605] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.433727] pci 0000:00:1d.7: PME# disabled
[    0.433921] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.433927] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[    0.434078] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH4 GPIO
[    0.434216] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.434223] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.434229] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.434236] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.434243] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    0.434249] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.434276] pci 0000:00:1f.2: reg 10 io port: [0xec00-0xec07]
[    0.434282] pci 0000:00:1f.2: reg 14 io port: [0xe800-0xe803]
[    0.434288] pci 0000:00:1f.2: reg 18 io port: [0xe400-0xe407]
[    0.434294] pci 0000:00:1f.2: reg 1c io port: [0xe000-0xe003]
[    0.434300] pci 0000:00:1f.2: reg 20 io port: [0xdc00-0xdc0f]
[    0.434349] pci 0000:00:1f.3: reg 20 io port: [0xc800-0xc81f]
[    0.434397] pci 0000:00:1f.5: reg 18 32bit mmio: [0xfd300400-0xfd3005ff]
[    0.434404] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xfd300800-0xfd3008ff]
[    0.434426] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.436007] pci 0000:00:1f.5: PME# disabled
[    0.436157] pci 0000:01:00.0: reg 10 32bit mmio: [0xf8000000-0xffffffff]
[    0.436163] pci 0000:01:00.0: reg 14 io port: [0xffffff00-0xffffffff]
[    0.436169] pci 0000:01:00.0: reg 18 32bit mmio: [0xffff0000-0xffffffff]
[    0.436185] pci 0000:01:00.0: reg 30 32bit mmio: [0xfffe0000-0xffffffff]
[    0.436196] pci 0000:01:00.0: supports D1 D2
[    0.436224] pci 0000:01:00.1: reg 10 32bit mmio: [0x000000-0x7ffffff]
[    0.436230] pci 0000:01:00.1: reg 14 32bit mmio: [0x000000-0x00ffff]
[    0.436256] pci 0000:01:00.1: supports D1 D2
[    0.436297] pci 0000:00:01.0: bridge io port: [0x9000-0x9fff]
[    0.436301] pci 0000:00:01.0: bridge 32bit mmio: [0xfa000000-0xfa0fffff]
[    0.436305] pci 0000:00:01.0: bridge 32bit mmio pref: [0xc0000000-0xcfffffff]
[    0.436359] pci 0000:02:03.0: supports D1
[    0.436361] pci 0000:02:03.0: PME# supported from D0 D1 D3hot
[    0.436481] pci 0000:02:03.0: PME# disabled
[    0.436627] pci 0000:02:04.0: reg 10 io port: [0xb800-0xb8ff]
[    0.436634] pci 0000:02:04.0: reg 14 32bit mmio: [0xfd102000-0xfd1020ff]
[    0.436665] pci 0000:02:04.0: supports D1 D2
[    0.436668] pci 0000:02:04.0: PME# supported from D1 D2 D3hot D3cold
[    0.436788] pci 0000:02:04.0: PME# disabled
[    0.436930] pci 0000:02:07.0: reg 10 32bit mmio: [0xfd100000-0xfd100fff]
[    0.436965] pci 0000:02:07.0: supports D1 D2
[    0.436967] pci 0000:02:07.0: PME# supported from D0 D1 D2 D3hot
[    0.437086] pci 0000:02:07.0: PME# disabled
[    0.437225] pci 0000:02:08.0: reg 10 32bit mmio: [0xfd101000-0xfd101fff]
[    0.437231] pci 0000:02:08.0: reg 14 io port: [0xbc00-0xbc3f]
[    0.437261] pci 0000:02:08.0: supports D1 D2
[    0.437263] pci 0000:02:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.437384] pci 0000:02:08.0: PME# disabled
[    0.437525] pci 0000:00:1e.0: transparent bridge
[    0.437641] pci 0000:00:1e.0: bridge io port: [0xa000-0xbfff]
[    0.437646] pci 0000:00:1e.0: bridge 32bit mmio: [0xfa000000-0xfd1fffff]
[    0.437651] pci 0000:00:1e.0: bridge 32bit mmio pref: [0xb0000000-0xcfffffff]
[    0.437720] pci 0000:03:00.0: reg 10 32bit mmio: [0xfc000000-0xfcffffff]
[    0.437743] pci 0000:03:00.0: reg 14 64bit mmio: [0xb0000000-0xbfffffff]
[    0.437766] pci 0000:03:00.0: reg 1c 64bit mmio: [0xfa000000-0xfbffffff]
[    0.437778] pci 0000:03:00.0: reg 24 io port: [0xac00-0xac7f]
[    0.437791] pci 0000:03:00.0: reg 30 32bit mmio: [0xfd000000-0xfd01ffff]
[    0.437867] pci 0000:02:03.0: bridge io port: [0xa000-0xafff]
[    0.437871] pci 0000:02:03.0: bridge 32bit mmio: [0xfa000000-0xfd0fffff]
[    0.437876] pci 0000:02:03.0: bridge 32bit mmio pref: [0xb0000000-0xcfffffff]
[    0.437894] bus 00 -> node 0
[    0.437901] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.438042] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.438138] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    0.441658] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.442906] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.444168] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.445412] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.446657] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.447901] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.449308] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.450704] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.451903] ACPI: Power Resource [URP1] (off)
[    0.452043] ACPI: Power Resource [FDDP] (off)
[    0.452194] ACPI: Power Resource [LPTP] (off)
[    0.452438] ACPI: WMI: Mapper loaded
[    0.452605] SCSI subsystem initialized
[    0.452605] libata version 3.00 loaded.
[    0.452605] usbcore: registered new interface driver usbfs
[    0.452605] usbcore: registered new interface driver hub
[    0.452605] usbcore: registered new device driver usb
[    0.452605] PCI: Using ACPI for IRQ routing
[    0.452605] pci 0000:00:1e.0: BAR 8: can't allocate resource
[    0.452605] pci 0000:00:1e.0: BAR 9: can't allocate resource
[    0.452605] pci 0000:02:03.0: BAR 8: can't allocate resource
[    0.452605] pci 0000:02:03.0: BAR 9: can't allocate resource
[    0.452636] pci 0000:00:00.0: BAR 0: can't allocate resource
[    0.452796] pci 0000:03:00.0: BAR 0: can't allocate resource
[    0.452913] pci 0000:03:00.0: BAR 1: can't allocate resource
[    0.453029] pci 0000:03:00.0: BAR 3: can't allocate resource
[    0.453173] pci 0000:01:00.0: BAR 0: can't allocate resource
[    0.453289] pci 0000:01:00.0: BAR 1: can't allocate resource
[    0.453406] pci 0000:01:00.0: BAR 2: can't allocate resource
[    0.460012] Bluetooth: Core ver 2.13
[    0.460139] NET: Registered protocol family 31
[    0.460139] Bluetooth: HCI device and connection manager initialized
[    0.460252] Bluetooth: HCI socket layer initialized
[    0.460366] NET: Registered protocol family 8
[    0.460478] NET: Registered protocol family 20
[    0.460602] NetLabel: Initializing
[    0.460712] NetLabel:  domain hash size = 128
[    0.460824] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.460950] NetLabel:  unlabeled traffic allowed by default
[    0.461150] hpet clockevent registered
[    0.461154] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.461278] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.461680] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.464070] AppArmor: AppArmor Filesystem Enabled
[    0.472012] pnp: PnP ACPI init
[    0.472130] ACPI: bus type pnp registered
[    0.474715] pnp 00:0a: io resource (0x10-0x1f) overlaps 0000:01:00.0 BAR 1 (0x0-0xff), disabling
[    0.474870] pnp 00:0a: io resource (0x22-0x3f) overlaps 0000:01:00.0 BAR 1 (0x0-0xff), disabling
[    0.475023] pnp 00:0a: io resource (0x44-0x4d) overlaps 0000:01:00.0 BAR 1 (0x0-0xff), disabling
[    0.475176] pnp 00:0a: io resource (0x50-0x5f) overlaps 0000:01:00.0 BAR 1 (0x0-0xff), disabling
[    0.475329] pnp 00:0a: io resource (0x62-0x63) overlaps 0000:01:00.0 BAR 1 (0x0-0xff), disabling
[    0.475482] pnp 00:0a: io resource (0x65-0x6f) overlaps 0000:01:00.0 BAR 1 (0x0-0xff), disabling
[    0.475636] pnp 00:0a: io resource (0x72-0x7f) overlaps 0000:01:00.0 BAR 1 (0x0-0xff), disabling
[    0.475789] pnp 00:0a: io resource (0x80-0x80) overlaps 0000:01:00.0 BAR 1 (0x0-0xff), disabling
[    0.475942] pnp 00:0a: io resource (0x84-0x86) overlaps 0000:01:00.0 BAR 1 (0x0-0xff), disabling
[    0.476113] pnp 00:0a: io resource (0x88-0x88) overlaps 0000:01:00.0 BAR 1 (0x0-0xff), disabling
[    0.476267] pnp 00:0a: io resource (0x8c-0x8e) overlaps 0000:01:00.0 BAR 1 (0x0-0xff), disabling
[    0.476420] pnp 00:0a: io resource (0x90-0x9f) overlaps 0000:01:00.0 BAR 1 (0x0-0xff), disabling
[    0.476573] pnp 00:0a: io resource (0xa2-0xbf) overlaps 0000:01:00.0 BAR 1 (0x0-0xff), disabling
[    0.476727] pnp 00:0a: io resource (0xe0-0xef) overlaps 0000:01:00.0 BAR 1 (0x0-0xff), disabling
[    0.477972] pnp 00:0d: mem resource (0x0-0x9ffff) overlaps 0000:00:00.0 BAR 0 (0x0-0xfffffff), disabling
[    0.478130] pnp 00:0d: mem resource (0xc0000-0xd7fff) overlaps 0000:00:00.0 BAR 0 (0x0-0xfffffff), disabling
[    0.478287] pnp 00:0d: mem resource (0xe0000-0xfffff) overlaps 0000:00:00.0 BAR 0 (0x0-0xfffffff), disabling
[    0.478444] pnp 00:0d: mem resource (0x100000-0x3fffffff) overlaps 0000:00:00.0 BAR 0 (0x0-0xfffffff), disabling
[    0.478615] pnp 00:0d: mem resource (0x0-0x9ffff) overlaps 0000:01:00.0 BAR 0 (0x0-0x7ffffff), disabling
[    0.478770] pnp 00:0d: mem resource (0xc0000-0xd7fff) overlaps 0000:01:00.0 BAR 0 (0x0-0x7ffffff), disabling
[    0.478927] pnp 00:0d: mem resource (0xe0000-0xfffff) overlaps 0000:01:00.0 BAR 0 (0x0-0x7ffffff), disabling
[    0.479083] pnp 00:0d: mem resource (0x100000-0x3fffffff) overlaps 0000:01:00.0 BAR 0 (0x0-0x7ffffff), disabling
[    0.479243] pnp 00:0d: mem resource (0x0-0x9ffff) overlaps 0000:01:00.1 BAR 0 (0x0-0x7ffffff), disabling
[    0.479398] pnp 00:0d: mem resource (0xc0000-0xd7fff) overlaps 0000:01:00.1 BAR 0 (0x0-0x7ffffff), disabling
[    0.479554] pnp 00:0d: mem resource (0xe0000-0xfffff) overlaps 0000:01:00.1 BAR 0 (0x0-0x7ffffff), disabling
[    0.479711] pnp 00:0d: mem resource (0x100000-0x3fffffff) overlaps 0000:01:00.1 BAR 0 (0x0-0x7ffffff), disabling
[    0.479874] pnp 00:0d: mem resource (0x0-0x9ffff) overlaps 0000:03:00.0 BAR 0 (0x0-0xffffff), disabling
[    0.480046] pnp 00:0d: mem resource (0xc0000-0xd7fff) overlaps 0000:03:00.0 BAR 0 (0x0-0xffffff), disabling
[    0.480202] pnp 00:0d: mem resource (0xe0000-0xfffff) overlaps 0000:03:00.0 BAR 0 (0x0-0xffffff), disabling
[    0.480358] pnp 00:0d: mem resource (0x100000-0x3fffffff) overlaps 0000:03:00.0 BAR 0 (0x0-0xffffff), disabling
[    0.480516] pnp 00:0d: mem resource (0x0-0x9ffff) overlaps 0000:03:00.0 BAR 1 (0x0-0xfffffff), disabling
[    0.480671] pnp 00:0d: mem resource (0xc0000-0xd7fff) overlaps 0000:03:00.0 BAR 1 (0x0-0xfffffff), disabling
[    0.480828] pnp 00:0d: mem resource (0xe0000-0xfffff) overlaps 0000:03:00.0 BAR 1 (0x0-0xfffffff), disabling
[    0.480984] pnp 00:0d: mem resource (0x100000-0x3fffffff) overlaps 0000:03:00.0 BAR 1 (0x0-0xfffffff), disabling
[    0.481142] pnp 00:0d: mem resource (0x0-0x9ffff) overlaps 0000:03:00.0 BAR 3 (0x0-0x1ffffff), disabling
[    0.481297] pnp 00:0d: mem resource (0xc0000-0xd7fff) overlaps 0000:03:00.0 BAR 3 (0x0-0x1ffffff), disabling
[    0.481454] pnp 00:0d: mem resource (0xe0000-0xfffff) overlaps 0000:03:00.0 BAR 3 (0x0-0x1ffffff), disabling
[    0.481611] pnp 00:0d: mem resource (0x100000-0x3fffffff) overlaps 0000:03:00.0 BAR 3 (0x0-0x1ffffff), disabling
[    0.482294] pnp: PnP ACPI: found 14 devices
[    0.482406] ACPI: ACPI bus type pnp unregistered
[    0.482522] PnPBIOS: Disabled by ACPI PNP
[    0.482647] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[    0.482771] system 00:0c: ioport range 0x400-0x47f has been reserved
[    0.482890] system 00:0c: ioport range 0x680-0x6ff has been reserved
[    0.483009] system 00:0c: ioport range 0x500-0x53f has been reserved
[    0.483129] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.483251] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.483372] system 00:0c: iomem range 0xfed20000-0xfed9ffff has been reserved
[    0.518237] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.518357] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.518475] pci 0000:00:01.0:   MEM window: 0xfa000000-0xfa0fffff
[    0.518595] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    0.518777] pci 0000:02:03.0: PCI bridge, secondary bus 0000:03
[    0.518895] pci 0000:02:03.0:   IO window: 0xa000-0xafff
[    0.519014] pci 0000:02:03.0:   MEM window: 0x68000000-0x6affffff
[    0.519134] pci 0000:02:03.0:   PREFETCH window: 0x00000050000000-0x00000067ffffff
[    0.519288] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.519406] pci 0000:00:1e.0:   IO window: 0xa000-0xbfff
[    0.519524] pci 0000:00:1e.0:   MEM window: 0x68000000-0x6affffff
[    0.519645] pci 0000:00:1e.0:   PREFETCH window: 0x00000050000000-0x00000067ffffff
[    0.519808] pci 0000:00:1e.0: setting latency timer to 64
[    0.519820] pci 0000:02:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.519943] bus: 00 index 0 io port: [0x00-0xffff]
[    0.520073] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.520190] bus: 01 index 0 io port: [0x9000-0x9fff]
[    0.520304] bus: 01 index 1 mmio: [0xfa000000-0xfa0fffff]
[    0.520420] bus: 01 index 2 mmio: [0xc0000000-0xcfffffff]
[    0.520535] bus: 01 index 3 mmio: [0x0-0x0]
[    0.520647] bus: 02 index 0 io port: [0xa000-0xbfff]
[    0.520761] bus: 02 index 1 mmio: [0x68000000-0x6affffff]
[    0.520877] bus: 02 index 2 mmio: [0x50000000-0x67ffffff]
[    0.520993] bus: 02 index 3 io port: [0x00-0xffff]
[    0.521107] bus: 02 index 4 mmio: [0x000000-0xffffffff]
[    0.521222] bus: 03 index 0 io port: [0xa000-0xafff]
[    0.521336] bus: 03 index 1 mmio: [0x68000000-0x6affffff]
[    0.521452] bus: 03 index 2 mmio: [0x50000000-0x67ffffff]
[    0.521568] bus: 03 index 3 mmio: [0x0-0x0]
[    0.521686] NET: Registered protocol family 2
[    0.536063] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.536489] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.536994] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.537363] TCP: Hash tables configured (established 131072 bind 65536)
[    0.537485] TCP reno registered
[    0.544097] NET: Registered protocol family 1
[    0.544353] checking if image is initramfs... it is
[    0.961464] Switched to high resolution mode on CPU 1
[    0.963973] Switched to high resolution mode on CPU 0
[    1.071661] Freeing initrd memory: 7367k freed
[    1.071985] cpufreq: No nForce2 chipset.
[    1.072243] audit: initializing netlink socket (disabled)
[    1.072382] type=2000 audit(1246528753.069:1): initialized
[    1.079493] highmem bounce pool size: 64 pages
[    1.079611] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.081153] VFS: Disk quotas dquot_6.5.1
[    1.081329] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.082135] fuse init (API version 7.10)
[    1.082341] msgmni has been set to 1724
[    1.082649] alg: No test for stdrng (krng)
[    1.082780] io scheduler noop registered
[    1.082892] io scheduler anticipatory registered
[    1.083005] io scheduler deadline registered
[    1.083132] io scheduler cfq registered (default)
[    1.083362] pci 0000:02:08.0: Firmware left e100 interrupts enabled; disabling
[    1.083545] pci 0000:03:00.0: Boot video device
[    1.086425] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.086551] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.086812] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.086963] ACPI: Power Button (FF) [PWRF]
[    1.087136] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    1.087293] ACPI: Sleep Button (CM) [SLPB]
[    1.087634] processor ACPI_CPU:00: registered as cooling_device0
[    1.087758] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.088098] processor ACPI_CPU:01: registered as cooling_device1
[    1.088219] ACPI: Processor [CPU2] (supports 8 throttling states)
[    1.090273] isapnp: Scanning for PnP cards...
[    1.441985] isapnp: No Plug & Play device found
[    1.449141] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.449341] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.449838] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.450860] brd: module loaded
[    1.451349] loop: module loaded
[    1.451534] Fixed MDIO Bus: probed
[    1.451647] PPP generic driver version 2.4.2
[    1.451823] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.452011] Driver 'sd' needs updating - please use bus_type methods
[    1.452140] Driver 'sr' needs updating - please use bus_type methods
[    1.452336] ata_piix 0000:00:1f.1: version 2.12
[    1.452345] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    1.452472] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.452629] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.452716] scsi0 : ata_piix
[    1.452938] scsi1 : ata_piix
[    1.454304] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.454426] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.616287] ata1.00: ATAPI: Memorex 48MAX 244816AJ, KWH8, max UDMA/33
[    1.632230] ata1.00: configured for UDMA/33
[    1.831092] ata2.00: ATA-7: MAXTOR STM3500630A, 3.AAE, max UDMA/100
[    1.831213] ata2.00: 976773168 sectors, multi 16: LBA48 
[    1.897720] ata2.00: configured for UDMA/100
[    1.898891] scsi 0:0:0:0: CD-ROM            Memorex  48MAX 244816AJ   KWH8 PQ: 0 ANSI: 5
[    1.903521] sr0: scsi3-mmc drive: 0x/48x writer cd/rw xa/form2 cdda tray
[    1.903644] Uniform CD-ROM driver Revision: 3.20
[    1.903866] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.903919] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.904131] scsi 1:0:0:0: Direct-Access     ATA      MAXTOR STM350063 3.AA PQ: 0 ANSI: 5
[    1.904385] sd 1:0:0:0: [sda] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    1.904554] sd 1:0:0:0: [sda] Write Protect is off
[    1.904669] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.904702] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.904918] sd 1:0:0:0: [sda] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    1.905085] sd 1:0:0:0: [sda] Write Protect is off
[    1.905200] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.905232] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.905388]  sda: sda1
[    1.937569] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.937728] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.937863] ata_piix 0000:00:1f.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.937987] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    1.938499] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.938584] scsi2 : ata_piix
[    1.938771] scsi3 : ata_piix
[    1.940110] ata3: SATA max UDMA/133 cmd 0xec00 ctl 0xe800 bmdma 0xdc00 irq 18
[    1.940233] ata4: SATA max UDMA/133 cmd 0xe400 ctl 0xe000 bmdma 0xdc08 irq 18
[    2.145321] ata3.00: ATA-7: ST3300622AS, 3.AAH, max UDMA/133
[    2.145439] ata3.00: 586072368 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.211973] ata3.00: configured for UDMA/133
[    2.407019] ata4.00: ATA-7: ST3300622AS, 3.AAH, max UDMA/133
[    2.407136] ata4.00: 586072368 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.490335] ata4.00: configured for UDMA/133
[    2.490534] scsi 2:0:0:0: Direct-Access     ATA      ST3300622AS      3.AA PQ: 0 ANSI: 5
[    2.490787] sd 2:0:0:0: [sdb] 586072368 512-byte hardware sectors: (300 GB/279 GiB)
[    2.490954] sd 2:0:0:0: [sdb] Write Protect is off
[    2.491069] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.491102] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.491318] sd 2:0:0:0: [sdb] 586072368 512-byte hardware sectors: (300 GB/279 GiB)
[    2.491484] sd 2:0:0:0: [sdb] Write Protect is off
[    2.491599] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.491631] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.491787]  sdb: sdb1 sdb2 < sdb5 sdb6 >
[    2.534840] sd 2:0:0:0: [sdb] Attached SCSI disk
[    2.535001] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    2.535198] scsi 3:0:0:0: Direct-Access     ATA      ST3300622AS      3.AA PQ: 0 ANSI: 5
[    2.535446] sd 3:0:0:0: [sdc] 586072368 512-byte hardware sectors: (300 GB/279 GiB)
[    2.535612] sd 3:0:0:0: [sdc] Write Protect is off
[    2.535727] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.535760] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.535971] sd 3:0:0:0: [sdc] 586072368 512-byte hardware sectors: (300 GB/279 GiB)
[    2.536161] sd 3:0:0:0: [sdc] Write Protect is off
[    2.536277] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.536312] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.536467]  sdc: sdc1
[    2.556698] sd 3:0:0:0: [sdc] Attached SCSI disk
[    2.556858] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    2.557741] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.557885] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    2.558029] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.558033] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.558214] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.562273] ehci_hcd 0000:00:1d.7: debug port 1
[    2.562391] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    2.562406] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfd300000
[    2.576011] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.576194] usb usb1: configuration #1 chosen from 1 choice
[    2.576340] hub 1-0:1.0: USB hub found
[    2.576458] hub 1-0:1.0: 8 ports detected
[    2.576697] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.576831] uhci_hcd: USB Universal Host Controller Interface driver
[    2.576983] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.577110] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.577113] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.577275] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.577448] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000cc00
[    2.577641] usb usb2: configuration #1 chosen from 1 choice
[    2.577786] hub 2-0:1.0: USB hub found
[    2.577903] hub 2-0:1.0: 2 ports detected
[    2.578106] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.578232] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.578236] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.578395] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.578573] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d000
[    2.578763] usb usb3: configuration #1 chosen from 1 choice
[    2.578907] hub 3-0:1.0: USB hub found
[    2.579023] hub 3-0:1.0: 2 ports detected
[    2.579233] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.579359] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.579363] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.579524] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.579690] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
[    2.579888] usb usb4: configuration #1 chosen from 1 choice
[    2.580054] hub 4-0:1.0: USB hub found
[    2.580171] hub 4-0:1.0: 2 ports detected
[    2.580373] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.580499] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.580503] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.580669] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    2.580836] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d800
[    2.581035] usb usb5: configuration #1 chosen from 1 choice
[    2.581179] hub 5-0:1.0: USB hub found
[    2.581295] hub 5-0:1.0: 2 ports detected
[    2.581560] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    2.585838] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.585959] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.592048] mice: PS/2 mouse device common for all mice
[    2.604071] rtc_cmos 00:02: RTC can wake from S4
[    2.604223] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    2.604363] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    2.604552] device-mapper: uevent: version 1.0.3
[    2.604779] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.605034] device-mapper: multipath: version 1.0.5 loaded
[    2.607645] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.607867] EISA: Probing bus 0 at eisa.0
[    2.608019] EISA: Detected 0 cards.
[    2.608202] cpuidle: using governor ladder
[    2.608316] cpuidle: using governor menu
[    2.609011] TCP cubic registered
[    2.609201] NET: Registered protocol family 10
[    2.609807] lo: Disabled Privacy Extensions
[    2.610341] NET: Registered protocol family 17
[    2.610476] Bluetooth: L2CAP ver 2.11
[    2.610587] Bluetooth: L2CAP socket layer initialized
[    2.610703] Bluetooth: SCO (Voice Link) ver 0.6
[    2.610815] Bluetooth: SCO socket layer initialized
[    2.610970] Bluetooth: RFCOMM socket layer initialized
[    2.611092] Bluetooth: RFCOMM TTY layer initialized
[    2.611206] Bluetooth: RFCOMM ver 1.10
[    2.611371] Using IPI No-Shortcut mode
[    2.611577] registered taskstats version 1
[    2.611818]   Magic number: 1:550:979
[    2.611996] rtc_cmos 00:02: setting system clock to 2009-07-02 09:59:14 UTC (1246528754)
[    2.612149] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.612266] EDD information not available.
[    2.612712] Freeing unused kernel memory: 532k freed
[    2.612966] Write protecting the kernel text: 4112k
[    2.613142] Write protecting the kernel read-only data: 1524k
[    2.635347] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.931537] Floppy drive(s): fd0 is 1.44M
[    2.951777] FDC 0 is a National Semiconductor PC87306
[    2.986909] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k6-NAPI
[    2.987009] e100: Copyright(c) 1999-2006 Intel Corporation
[    2.987188] e100 0000:02:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.010067] e100 0000:02:08.0: PME# disabled
[    3.013870] e100: eth0: e100_probe: addr 0xfd101000, irq 20, MAC addr 00:11:11:b3:4c:c0
[    3.014034] ohci1394 0000:02:07.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.020961] 8139too Fast Ethernet driver 0.9.28
[    3.066026] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[17]  MMIO=[fd100000-fd1007ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    3.080764] 8139too 0000:02:04.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.082477] eth1: RealTek RTL8139 at 0xb800, 00:0d:88:3b:bd:4c, IRQ 18
[    3.082577] eth1:  Identified 8139 chip type 'RTL-8100B/8139D'
[    3.477562] PM: Starting manual resume from disk
[    3.477653] PM: Resume from partition 8:22
[    3.477655] PM: Checking hibernation image.
[    3.477818] PM: Resume from disk failed.
[    3.506692] kjournald starting.  Commit interval 5 seconds
[    3.506793] EXT3-fs: mounted filesystem with ordered data mode.
[    4.348177] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011110000b34cc0]
[    9.261810] udev: starting version 141
[    9.481944] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    9.696867] udev: renamed network interface eth0 to eth1
[    9.741952] udev: renamed network interface eth1_rename to eth0
[    9.772075] Linux agpgart interface v0.103
[    9.804831] agpgart-intel 0000:00:00.0: Intel 865 Chipset
[    9.814616] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x70000000
[    9.829436] intel_rng: Firmware space is locked read-only. If you can't or
[    9.829439] intel_rng: don't want to disable this in firmware setup, and if
[    9.829441] intel_rng: you are certain that your system has a functional
[    9.829443] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   10.136849] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   10.170862] parport_pc 00:09: reported by Plug and Play ACPI
[   10.171051] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   10.518089] nvidia: module license 'NVIDIA' taints kernel.
[   10.616811] ppdev: user-space parallel port driver
[   10.660954] iTCO_vendor_support: vendor-support=0
[   10.690731] ip_tables: (C) 2000-2006 Netfilter Core Team
[   10.693305] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   10.693580] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0460)
[   10.693828] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   10.739723] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   10.775039] nvidia 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   10.775175] nvidia 0000:03:00.0: setting latency timer to 64
[   10.775671] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
[   10.839512] nf_conntrack version 0.5.0 (16355 buckets, 65420 max)
[   10.840022] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   10.840182] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   10.840341] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   11.039862] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   11.040140] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   11.251583] psmouse serio1: ID: 10 00 64<6>intel8x0_measure_ac97_clock: measured 52174 usecs
[   11.460021] intel8x0: clocking to 48000
[   11.619313] lp0: using parport0 (interrupt-driven).
[   11.709306] Adding 2136604k swap on /dev/sdb6.  Priority:-1 extents:1 across:2136604k
[   11.819107] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input5
[   12.054706] EXT3 FS on sdb5, internal journal
[   12.695210] type=1505 audit(1246553964.580:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2094
[   12.741834] type=1505 audit(1246553964.628:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2098
[   12.741966] type=1505 audit(1246553964.628:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2098
[   12.742012] type=1505 audit(1246553964.628:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2098
[   12.742055] type=1505 audit(1246553964.628:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2098
[   12.870766] type=1505 audit(1246553964.756:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2103
[   12.870945] type=1505 audit(1246553964.756:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2103
[   12.905307] type=1505 audit(1246553964.792:9): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2107
[   12.933226] type=1505 audit(1246553964.820:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2111
[   13.300949] RPC: Registered udp transport module.
[   13.300955] RPC: Registered tcp transport module.
[   13.400473] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   18.263664] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   18.288340] NFSD: starting 90-second grace period
[   20.221336] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.221343] Bluetooth: BNEP filters: protocol multicast
[   20.252909] Bridge firewalling registered
[   25.141287] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   25.142372] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   25.144141] e100: eth1: e100_watchdog: link up, 100Mbps, full-duplex
[   25.149981] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   35.148008] eth0: no IPv6 routers present
[   35.240017] eth1: no IPv6 routers present


```

---

### Post by configt on 2009-07-02
> **metiosarius said:**
> There is an outstanding issue with some systems where you have to press random keys or move the mouse around in order to get the boot/shutdown process to continue. As far as I know, there is no solution at the moment other than pressing keys. Give it a try...

Is this issue documented somewhere?  Link?

Thanks.

---

### Post by configt on 2009-07-06
It would be nice to be able to do something basic and simple like shutting down my computer.

---

### Post by configt on 2009-07-18
Any help would be greatly appreciated.  Not being able to shutdown my computer is getting to be very inconvenient.

](*,)

---

### Post by etsoft.be on 2009-08-23
try to add in /boot/grub/menu.lst acpi=off in the kernel parameter list.

kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=dab4a037-69a9-4930-9c08-2848bec4d437 ro quiet splash acpi=off 

that did the job!

greets,

Etsoft

---

### Post by mvalenti on 2009-10-24
Newbie here similar issue, how do I add those?

---

### Post by RJARRRPCGP on 2009-10-24
> **metiosarius said:**
> There is an outstanding issue with some systems where you have to press random keys or move the mouse around in order to get the boot/shutdown process to continue. As far as I know, there is no solution at the moment other than pressing keys. Give it a try...

Reminds me of the strange QEMU bug when installing XP on QEMU. (where XP setup looks like it locked up)

---

### Post by mvalenti on 2009-10-25
I started having this issue after getting blueman working an then attempting to get flash working. I removed all flash packages and reinstalled flash, system is shutting down fine now.


-Mark

---

