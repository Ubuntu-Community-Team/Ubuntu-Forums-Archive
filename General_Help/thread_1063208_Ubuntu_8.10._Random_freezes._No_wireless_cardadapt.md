---
title: "Ubuntu 8.10. Random freezes. No wireless card/adapter."
date: 2009-02-07
forum: General Help
---

### Post by Fazz Munkle on 2009-02-07
NO wireless card is being used on this computer. I've seen many people say this is because of wireless cards. I don't have one, so that's not it for me.

Latest upgrades to 8.10.

Remember: No wireless card is being used.

I have:
Asus A7N8X-E Deluxe
Athlon 3200+
2GB Corsair RAM (memtest86 says everything's alright)
XFX Force nVidia GeForce 6200 256MB
75GB WD SATA hard drive in a USB/eSATA enclosure, boot drive (using USB connection for now)
A Kensington USB 2.0 hub with HP PhotoSmart D7160 connected
Logitech MX Revolution mouse
Old Dell CRT
Regular PS/2 keyboard

Problem:
Computer freezes with the caps lock and scroll lock flashing. May happen an hour after boot up, may go for days before freezing, may happen as soon as GNOME loads. This has happened to me at least 30-40 times already over the last 3 months. No response at all from the computer. I have to hard reboot. The reboot before last I was unable to boot into any drive I used. It seemed to try to boot from a nonexistent network drive for some reason and then returned a failure with something (either chipset or BIOS, I can't remember). Had to restore BIOS defaults to fix things. This hadn't happened before. Now it seems to boot fine. This is up 'til _now_.

Can someone please help me? Either point me in the right direction towards the correct answer? Or at least let me know what is being done about this and will it be fixed by Ubuntu 9.0x? My problem seems pretty similar to those who think this is a wireless card problem, yet their problems aren't quite answered for them (or at least their solutions don't apply to my situation).

Please help.

---

### Post by kayvortex on 2009-02-07
The caps and scroll lock lights blinking means that there's been a kernel panic, which is normally a hardware related problem.

You'll have to track down what hardware is causing it. You can issue:
```
sudo lshw
```
to print your hardware and then search to see if there are any reported conflicts of bits of hardware with your kernel version.
```
uname -r
```
will tell you your kernel version.
You might also be able to find error outputs in your system logs files, so maybe post them up. Click on System -> Administration -> System Log.

You could also try detaching non-critical hardware that you suspect might be causing it, and even try updating the drivers for your hardware.

---

### Post by Fazz Munkle on 2009-02-08
I'll go through this tonight myself, but here's the print out for you to see in case I miss anything. I'm no debugging master so I may not know what I'm looking for. I see "error" and I wonder if that's something for instance. ;)

```
****-desktop              
    description: Desktop Computer
    product: A7N8X-E
    vendor: ASUSTeK Computer INC.
    version: REV 2.xx
    serial: xxxxxxxxxxx
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2 smp
    configuration: boot=normal chassis=desktop uuid=803770FB-A7DE-0F10-9195-F91EF0FB7679
  *-core
       description: Motherboard
       product: A7N8X-E
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: REV 2.xx
       serial: xxxxxxxxxxx
       slot: Serial Port 1
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: ASUS A7N8X-E Deluxe ACPI BIOS Rev 1013 (11/12/2004)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 3200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.10.0
          slot: Socket A
          size: 2200MHz
          capacity: 3GHz
          width: 32 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: pipeline-burst synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: a
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst synchronous external write-back data
     *-memory
          description: System Memory
          physical id: 26
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DRAM Synchronous [empty]
             physical id: 0
             slot: DDR1
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: DDR2
             size: 1GiB
             width: 64 bits
        *-bank:2
             description: DIMM DRAM Synchronous
             physical id: 2
             slot: DDR3
             size: 1GiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: nForce2 IGP2
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: c1
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-nvidia module=nvidia_agp
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 1
             vendor: nVidia Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 4
             vendor: nVidia Corporation
             physical id: 0.2
             bus info: pci@0000:00:00.2
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 3
             vendor: nVidia Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:3 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 2
             vendor: nVidia Corporation
             physical id: 0.4
             bus info: pci@0000:00:00.4
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:4 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 5
             vendor: nVidia Corporation
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: nForce2 ISA Bridge
             vendor: nVidia Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: isa ht bus_master cap_list
             configuration: latency=0
        *-serial
             description: SMBus
             product: nForce2 SMBus (MCP)
             vendor: nVidia Corporation
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: pm cap_list
             configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3 module=i2c_nforce2
        *-usb:0
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2.2
             bus info: pci@0000:00:02.2
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: debug pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
        *-network
             description: Ethernet interface
             product: nForce2 Ethernet Controller
             vendor: nVidia Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: a1
             serial: 00:11:d8:83:86:e8
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.1.4 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
        *-multimedia:0 UNCLAIMED
             description: Multimedia audio controller
             product: nForce Audio Processing Unit
             vendor: nVidia Corporation
             physical id: 5
             bus info: pci@0000:00:05.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0 maxlatency=12 mingnt=1
        *-multimedia:1
             description: Multimedia audio controller
             product: nForce2 AC97 Audio Controler (MCP)
             vendor: nVidia Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0
        *-pci:0
             description: PCI bridge
             product: nForce2 External PCI Bridge
             vendor: nVidia Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-network
                description: Ethernet interface
                product: 88E8001 Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 4
                bus info: pci@0000:01:04.0
                logical name: eth1
                version: 13
                serial: 00:11:d8:82:76:cb
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 firmware=N/A latency=32 link=no maxlatency=31 mingnt=23 module=skge multicast=yes port=twisted pair
           *-storage
                description: RAID bus controller
                product: SiI 3112 [SATALink/SATARaid] Serial ATA Controller
                vendor: Silicon Image, Inc.
                physical id: b
                bus info: pci@0000:01:0b.0
                version: 02
                width: 32 bits
                clock: 66MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=sata_sil latency=32 module=sata_sil
        *-ide
             description: IDE interface
             product: nForce2 IDE
             vendor: nVidia Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3 module=pata_amd
        *-firewire
             description: FireWire (IEEE 1394)
             product: nForce2 FireWire (IEEE 1394) Controller
             vendor: nVidia Corporation
             physical id: d
             bus info: pci@0000:00:0d.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci1394 latency=0 maxlatency=1 mingnt=3 module=ohci1394
        *-pci:1
             description: PCI bridge
             product: nForce2 AGP
             vendor: nVidia Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c1
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-display
                description: VGA compatible controller
                product: NV44A [GeForce 6200]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
     *-scsi:0
          physical id: 1
          bus info: usb@3:3
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sda
             size: 74GiB (80GB)
             capabilities: partitioned partitioned:dos
             configuration: signature=cfce3150
           *-volume:0
                description: EXT3 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                logical name: /dev/.static/dev
                version: 1.0
                serial: 7c889f05-fb15-4d69-ad10-16d5d0c36fc9
                size: 70GiB
                capacity: 70GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                configuration: created=2008-12-29 02:44:15 filesystem=ext3 modified=2009-02-07 15:38:41 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2009-02-07 10:55:13 state=mounted
           *-volume:1
                description: Linux swap volume
                physical id: 2
                bus info: scsi@4:0.0.0,2
                logical name: /dev/sda2
                version: 1
                serial: 51f8e3ad-32c3-4327-b492-e1953b301d1b
                size: 4118MiB
                capacity: 4118MiB
                capabilities: primary nofs swap initialized
                configuration: filesystem=swap pagesize=4096
     *-scsi:1
          physical id: 2
          bus info: usb@3:5.4
          logical name: scsi5
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Photosmart D7100
             vendor: HP
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/sdb
             version: 1.00
             capabilities: removable
             configuration: ansiversion=2
           *-medium
                physical id: 0
                logical name: /dev/sdb
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 7e:3d:ef:70:b5:af
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

Here's the kernel version:
2.6.27-11-generic

Looking at the log list I can't pinpoint when I had the crash, but if it happens again I'll post it now that I know where to get it.

---

### Post by kayvortex on 2009-02-08
Well, I'm looking suspiciously at
> *-storage
                description: RAID bus controller
                product: SiI 3112 [SATALink/SATARaid] Serial ATA Controller
                vendor: Silicon Image, Inc.

Googling around I see talk about problems with SiI 3112 host controller (and also things about nForce2), but I'm not nearly experienced enough when it comes to the specifics of what exactly is going on. From what I think I can piece together is that your SiI driver is causing the problems, but I'm not exactly sure how to resolve it: I'd imagine that you might ultimately have to patch your kernel with an update, but where to get that update, I don't know.

One thing that you could try (and this is a blind stab in the dark) is maybe try adding the "noapic" option as a boot parameter: when your system boots up and the grub menu shows up, press 'e' before the timeout. This will show you some info on the partition you're trying to boot from. Press 'e' again and add "noapic" to the end of the line that comes up. Press Enter to make the change and then press 'b' to boot (N.B. don't press anything else, not even the cursor keys!). This will add the noapic option for this particular bootup: it will not be saved; so, you'll have to repeat this every time you boot up (we *can* make the change permanent, but let's make sure it actually does something first!).

Also, could you post the output of dmesg: that will show what the kernel is up to:
```
dmesg > ~/dmesg.out
```
And then the file dmesg.out in your home folder will contain dmesg's output.

---

### Post by Fazz Munkle on 2009-02-08
I suspect the change would be in the menu.lst file? I'll try this and use my computer as normal and see what happens.

When I added noapic to the end of the line I put a space before it as the cursor was right at the end of the last character in the line. I hope this was the right thing to do. I didn't think that the option would have been recognized if I just tacked it on to the end and probably would have messed up the previous command on the line. It doesn't seem to have done anything bad so I'll wait and see.

Here's the output.

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fff0000 (usable)
[    0.000000]  BIOS-e820: 000000007fff0000 - 000000007fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff3000 - 0000000080000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.2 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x7fff0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 10000-15000
[    0.000000] RAMDISK: 3782c000 - 37fefc69
[    0.000000] ACPI: RSDP 000F75E0, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 7FFF3000, 002C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 7FFF3040, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 7FFF30C0, 4561 (r1 NVIDIA AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 7FFF0000, 0040
[    0.000000] ACPI: APIC 7FFF7640, 006E (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00011000 - 00018000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
[    0.000000]   #4 [003782c000 - 0037fefc69]          RAMDISK ==> [003782c000 - 0037fefc69]
[    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
[    0.000000]   #6 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0007fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x000000a0
[    0.000000]     0: 0x00000100 -> 0x0007fff0
[    0.000000] On node 0 totalpages: 524160
[    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000240
[    0.000000]   DMA zone: 3948 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 292304 pages, LIFO batch:31
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ec00000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519552
[    0.000000] Kernel command line: root=UUID=7c889f05-fb15-4d69-ad10-16d5d0c36fc9 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2191.195 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 2063616k/2097088k available (2576k kernel code, 32172k reserved, 1165k data, 424k init, 1179584k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
[    0.004000]       .data : 0xc03840da - 0xc04a7680   (1165 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03840da   (2576 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004012] Calibrating delay loop (skipped), value calculated using timer frequency.. 4382.39 BogoMIPS (lpj=8764780)
[    0.004035] Security Framework initialized
[    0.004043] SELinux:  Disabled at boot.
[    0.004071] AppArmor: AppArmor initialized
[    0.004080] Mount-cache hash table entries: 512
[    0.004257] Initializing cgroup subsys ns
[    0.004261] Initializing cgroup subsys cpuacct
[    0.004264] Initializing cgroup subsys memory
[    0.004279] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004282] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004295] Checking 'hlt' instruction... OK.
[    0.020289] SMP alternatives: switching to UP code
[    0.024022] Freeing SMP alternatives: 11k freed
[    0.024025] ACPI: Core revision 20080609
[    0.025329] ACPI: Checking initramfs for custom DSDT
[    0.328264] ENABLING IO-APIC IRQs
[    0.328451] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.372567] CPU0: AMD Athlon(tm) XP 3200+ stepping 00
[    0.376023] Brought up 1 CPUs
[    0.376023] Total of 1 processors activated (4382.39 BogoMIPS).
[    0.376023] CPU0 attaching NULL sched-domain.
[    0.376023] net_namespace: 840 bytes
[    0.376023] Booting paravirtualized kernel on bare hardware
[    0.376023] Time: 18:53:28  Date: 02/08/09
[    0.376023] NET: Registered protocol family 16
[    0.376023] EISA bus registered
[    0.376023] ACPI: bus type pci registered
[    0.404730] PCI: PCI BIOS revision 2.10 entry at 0xfb410, last bus=3
[    0.404733] PCI: Using configuration type 1 for base access
[    0.406755] ACPI: EC: Look up EC in DSDT
[    0.414517] ACPI: Interpreter enabled
[    0.414522] ACPI: (supports S0 S1 S4 S5)
[    0.414538] ACPI: Using IOAPIC for interrupt routing
[    0.425474] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.425549] PCI: 0000:00:00.0 reg 10 32bit mmio: [e0000000, e3ffffff]
[    0.425567] pci 0000:00:00.0: nForce2 C1 Halt Disconnect fixup
[    0.425724] PCI: 0000:00:01.1 reg 10 io port: [e000, e01f]
[    0.425755] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.425760] pci 0000:00:01.1: PME# disabled
[    0.425785] PCI: 0000:00:02.0 reg 10 32bit mmio: [ea087000, ea087fff]
[    0.425815] pci 0000:00:02.0: supports D1
[    0.425817] pci 0000:00:02.0: supports D2
[    0.425819] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.425823] pci 0000:00:02.0: PME# disabled
[    0.425843] PCI: 0000:00:02.1 reg 10 32bit mmio: [ea082000, ea082fff]
[    0.425874] pci 0000:00:02.1: supports D1
[    0.425876] pci 0000:00:02.1: supports D2
[    0.425878] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.425882] pci 0000:00:02.1: PME# disabled
[    0.425908] PCI: 0000:00:02.2 reg 10 32bit mmio: [ea083000, ea0830ff]
[    0.425942] pci 0000:00:02.2: supports D1
[    0.425944] pci 0000:00:02.2: supports D2
[    0.425946] pci 0000:00:02.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.425951] pci 0000:00:02.2: PME# disabled
[    0.425975] PCI: 0000:00:04.0 reg 10 32bit mmio: [ea086000, ea086fff]
[    0.425981] PCI: 0000:00:04.0 reg 14 io port: [e400, e407]
[    0.426009] pci 0000:00:04.0: supports D1
[    0.426010] pci 0000:00:04.0: supports D2
[    0.426012] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.426016] pci 0000:00:04.0: PME# disabled
[    0.426037] PCI: 0000:00:05.0 reg 10 32bit mmio: [ea000000, ea07ffff]
[    0.426067] pci 0000:00:05.0: supports D1
[    0.426069] pci 0000:00:05.0: supports D2
[    0.426089] PCI: 0000:00:06.0 reg 10 io port: [d000, d0ff]
[    0.426094] PCI: 0000:00:06.0 reg 14 io port: [d400, d47f]
[    0.426100] PCI: 0000:00:06.0 reg 18 32bit mmio: [ea080000, ea080fff]
[    0.426124] pci 0000:00:06.0: supports D1
[    0.426126] pci 0000:00:06.0: supports D2
[    0.426178] PCI: 0000:00:09.0 reg 20 io port: [f000, f00f]
[    0.426217] PCI: 0000:00:0d.0 reg 10 32bit mmio: [ea084000, ea0847ff]
[    0.426223] PCI: 0000:00:0d.0 reg 14 32bit mmio: [ea085000, ea08503f]
[    0.426250] pci 0000:00:0d.0: supports D1
[    0.426252] pci 0000:00:0d.0: supports D2
[    0.426254] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.426258] pci 0000:00:0d.0: PME# disabled
[    0.426332] PCI: 0000:01:04.0 reg 10 32bit mmio: [e9000000, e9003fff]
[    0.426339] PCI: 0000:01:04.0 reg 14 io port: [a000, a0ff]
[    0.426366] PCI: 0000:01:04.0 reg 30 32bit mmio: [0, 1ffff]
[    0.426382] pci 0000:01:04.0: supports D1
[    0.426384] pci 0000:01:04.0: supports D2
[    0.426386] pci 0000:01:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.426390] pci 0000:01:04.0: PME# disabled
[    0.426426] PCI: 0000:01:0b.0 reg 10 io port: [a400, a407]
[    0.426434] PCI: 0000:01:0b.0 reg 14 io port: [a800, a803]
[    0.426441] PCI: 0000:01:0b.0 reg 18 io port: [ac00, ac07]
[    0.426448] PCI: 0000:01:0b.0 reg 1c io port: [b000, b003]
[    0.426455] PCI: 0000:01:0b.0 reg 20 io port: [b400, b40f]
[    0.426463] PCI: 0000:01:0b.0 reg 24 32bit mmio: [e9004000, e90041ff]
[    0.426470] PCI: 0000:01:0b.0 reg 30 32bit mmio: [0, 7ffff]
[    0.426484] pci 0000:01:0b.0: supports D1
[    0.426486] pci 0000:01:0b.0: supports D2
[    0.426516] PCI: bridge 0000:00:08.0 io port: [a000, bfff]
[    0.426520] PCI: bridge 0000:00:08.0 32bit mmio: [e8000000, e9ffffff]
[    0.426551] PCI: 0000:03:00.0 reg 10 32bit mmio: [e5000000, e5ffffff]
[    0.426556] PCI: 0000:03:00.0 reg 14 32bit mmio: [d0000000, dfffffff]
[    0.426562] PCI: 0000:03:00.0 reg 18 32bit mmio: [e6000000, e6ffffff]
[    0.426577] PCI: 0000:03:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.426619] PCI: bridge 0000:00:1e.0 32bit mmio: [e5000000, e7ffffff]
[    0.426623] PCI: bridge 0000:00:1e.0 32bit mmio pref: [d0000000, dfffffff]
[    0.426633] bus 00 -> node 0
[    0.426641] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.426869] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.427308] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[    0.494264] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.494468] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.494669] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.494869] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.495068] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.495275] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[    0.495475] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.495675] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.495875] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[    0.496219] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.496420] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.496621] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.496823] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.497022] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.497220] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.497419] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.497593] ACPI: PCI Interrupt Link [APC1] (IRQs *16), disabled.
[    0.497748] ACPI: PCI Interrupt Link [APC2] (IRQs *17)
[    0.497903] ACPI: PCI Interrupt Link [APC3] (IRQs *18)
[    0.498058] ACPI: PCI Interrupt Link [APC4] (IRQs *19)
[    0.498212] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[    0.498437] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
[    0.498661] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0
[    0.498884] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0
[    0.499107] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0
[    0.499329] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0
[    0.499551] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
[    0.499709] ACPI: PCI Interrupt Link [APCS] (IRQs *23)
[    0.499930] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
[    0.500162] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0
[    0.500386] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
[    0.500609] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
[    0.500805] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.500847] pnp: PnP ACPI init
[    0.500855] ACPI: bus type pnp registered
[    0.507575] pnp: PnP ACPI: found 16 devices
[    0.507578] ACPI: ACPI bus type pnp unregistered
[    0.507582] PnPBIOS: Disabled by ACPI PNP
[    0.508010] PCI: Using ACPI for IRQ routing
[    0.508155] NET: Registered protocol family 8
[    0.508155] NET: Registered protocol family 20
[    0.508155] NetLabel: Initializing
[    0.508155] NetLabel:  domain hash size = 128
[    0.508155] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.508155] NetLabel:  unlabeled traffic allowed by default
[    0.508383] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.508386]    actual entries 65620
[    0.508567] AppArmor: AppArmor Filesystem Enabled
[    0.508591] ACPI: RTC can wake from S4
[    0.508598] system 00:00: ioport range 0x4000-0x407f has been reserved
[    0.508598] system 00:00: ioport range 0x4080-0x40ff has been reserved
[    0.508598] system 00:00: ioport range 0x4400-0x447f has been reserved
[    0.508598] system 00:00: ioport range 0x4480-0x44ff has been reserved
[    0.508598] system 00:00: ioport range 0x4200-0x427f has been reserved
[    0.508598] system 00:00: ioport range 0x4280-0x42ff has been reserved
[    0.508598] system 00:01: ioport range 0x5000-0x503f has been reserved
[    0.508598] system 00:01: ioport range 0x5500-0x553f has been reserved
[    0.508598] system 00:02: iomem range 0xd7000-0xd7fff has been reserved
[    0.508598] system 00:02: iomem range 0xf0000-0xf7fff could not be reserved
[    0.508598] system 00:02: iomem range 0xf8000-0xfbfff could not be reserved
[    0.508598] system 00:02: iomem range 0xfc000-0xfffff could not be reserved
[    0.508598] system 00:02: iomem range 0x7fff0000-0x7fffffff could not be reserved
[    0.508598] system 00:02: iomem range 0xffff0000-0xffffffff could not be reserved
[    0.508598] system 00:02: iomem range 0x0-0x9ffff could not be reserved
[    0.508598] system 00:02: iomem range 0x100000-0x7ffeffff could not be reserved
[    0.508598] system 00:02: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.508598] system 00:02: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.508598] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.543975] pci 0000:00:08.0: PCI bridge, secondary bus 0000:01
[    0.543979] pci 0000:00:08.0:   IO window: 0xa000-0xbfff
[    0.543985] pci 0000:00:08.0:   MEM window: 0xe8000000-0xe9ffffff
[    0.543990] pci 0000:00:08.0:   PREFETCH window: 0x00000088000000-0x000000880fffff
[    0.543997] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.543999] pci 0000:00:1e.0:   IO window: disabled
[    0.544003] pci 0000:00:1e.0:   MEM window: 0xe5000000-0xe7ffffff
[    0.544008] pci 0000:00:1e.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.544021] pci 0000:00:08.0: setting latency timer to 64
[    0.544027] bus: 00 index 0 io port: [0, ffff]
[    0.544035] bus: 00 index 1 mmio: [0, ffffffff]
[    0.544037] bus: 01 index 0 io port: [a000, bfff]
[    0.544039] bus: 01 index 1 mmio: [e8000000, e9ffffff]
[    0.544042] bus: 01 index 2 mmio: [88000000, 880fffff]
[    0.544044] bus: 01 index 3 mmio: [0, 0]
[    0.544046] bus: 03 index 0 mmio: [0, 0]
[    0.544048] bus: 03 index 1 mmio: [e5000000, e7ffffff]
[    0.544050] bus: 03 index 2 mmio: [d0000000, dfffffff]
[    0.544052] bus: 03 index 3 mmio: [0, 0]
[    0.544062] NET: Registered protocol family 2
[    0.544183] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.544517] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.545700] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.546315] TCP: Hash tables configured (established 131072 bind 65536)
[    0.546318] TCP reno registered
[    0.546428] NET: Registered protocol family 1
[    0.546564] checking if image is initramfs... it is
[    1.044087] Switched to high resolution mode on CPU 0
[    1.194655] Freeing initrd memory: 7951k freed
[    1.195476] audit: initializing netlink socket (disabled)
[    1.195494] type=2000 audit(1234119208.192:1): initialized
[    1.200842] highmem bounce pool size: 64 pages
[    1.200849] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.203334] VFS: Disk quotas dquot_6.5.1
[    1.203422] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.203528] msgmni has been set to 1743
[    1.203662] io scheduler noop registered
[    1.203665] io scheduler anticipatory registered
[    1.203667] io scheduler deadline registered
[    1.203679] io scheduler cfq registered (default)
[    1.256090] pci 0000:03:00.0: Boot video device
[    1.256451] isapnp: Scanning for PnP cards...
[    1.610626] isapnp: No Plug & Play device found
[    1.652971] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.653116] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.653286] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.653966] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.654310] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.656516] brd: module loaded
[    1.656590] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.656710] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.656714] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.657154] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.657505] mice: PS/2 mouse device common for all mice
[    1.657657] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.657679] rtc0: alarms up to one year, y3k
[    1.657811] EISA: Probing bus 0 at eisa.0
[    1.657833] Cannot allocate resource for EISA slot 4
[    1.657835] Cannot allocate resource for EISA slot 5
[    1.657850] EISA: Detected 0 cards.
[    1.657853] cpuidle: using governor ladder
[    1.657856] cpuidle: using governor menu
[    1.658384] TCP cubic registered
[    1.658412] Using IPI No-Shortcut mode
[    1.658616] registered taskstats version 1
[    1.658743]   Magic number: 13:822:897
[    1.658825] tty ptyy7: hash matches
[    1.658836] tty ptyva: hash matches
[    1.658922] rtc_cmos 00:06: setting system clock to 2009-02-08 18:53:29 UTC (1234119209)
[    1.658926] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.658928] EDD information not available.
[    1.659333] Freeing unused kernel memory: 424k freed
[    1.659388] Write protecting the kernel text: 2580k
[    1.659423] Write protecting the kernel read-only data: 940k
[    1.686071] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.916036] fuse init (API version 7.9)
[    2.168017] processor ACPI0007:00: registered as cooling_device0
[    3.272085] usbcore: registered new interface driver usbfs
[    3.272112] usbcore: registered new interface driver hub
[    3.283111] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    3.283501] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[    3.283511] forcedeth 0000:00:04.0: PCI INT A -> Link[APCH] -> GSI 22 (level, high) -> IRQ 22
[    3.283517] forcedeth 0000:00:04.0: setting latency timer to 64
[    3.283547] nv_probe: set workaround bit for reversed mac addr
[    3.291309] usbcore: registered new device driver usb
[    3.293548] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.312116] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    3.330357] No dock devices found.
[    3.377834] SCSI subsystem initialized
[    3.459295] libata version 3.00 loaded.
[    3.800654] forcedeth 0000:00:04.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:11:d8:83:86:e8
[    3.800659] forcedeth 0000:00:04.0: timirq lnktim desc-v1
[    3.801163] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[    3.801173] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 21 (level, high) -> IRQ 21
[    3.801190] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    3.801193] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    3.801243] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[    3.801268] ohci_hcd 0000:00:02.0: irq 21, io mem 0xea087000
[    3.858210] usb usb1: configuration #1 chosen from 1 choice
[    3.858241] hub 1-0:1.0: USB hub found
[    3.858255] hub 1-0:1.0: 3 ports detected
[    4.064654] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 20
[    4.064664] ohci_hcd 0000:00:02.1: PCI INT B -> Link[APCG] -> GSI 20 (level, high) -> IRQ 20
[    4.064679] ohci_hcd 0000:00:02.1: setting latency timer to 64
[    4.064683] ohci_hcd 0000:00:02.1: OHCI Host Controller
[    4.064709] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[    4.064733] ohci_hcd 0000:00:02.1: irq 20, io mem 0xea082000
[    4.122183] usb usb2: configuration #1 chosen from 1 choice
[    4.122215] hub 2-0:1.0: USB hub found
[    4.122227] hub 2-0:1.0: 3 ports detected
[    4.240012] usb 1-2: new full speed USB device using ohci_hcd and address 2
[    4.328622] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[    4.328629] ehci_hcd 0000:00:02.2: PCI INT C -> Link[APCL] -> GSI 22 (level, high) -> IRQ 22
[    4.328644] ehci_hcd 0000:00:02.2: setting latency timer to 64
[    4.328648] ehci_hcd 0000:00:02.2: EHCI Host Controller
[    4.328676] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[    4.328717] ehci_hcd 0000:00:02.2: debug port 1
[    4.328722] ehci_hcd 0000:00:02.2: cache line size of 64 is not supported
[    4.328738] ehci_hcd 0000:00:02.2: irq 22, io mem 0xea083000
[    4.428009] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.428186] usb usb3: configuration #1 chosen from 1 choice
[    4.428216] hub 3-0:1.0: USB hub found
[    4.428226] hub 3-0:1.0: 6 ports detected
[    4.636666] ACPI: PCI Interrupt Link [APCM] enabled at IRQ 21
[    4.636673] ohci1394 0000:00:0d.0: PCI INT A -> Link[APCM] -> GSI 21 (level, high) -> IRQ 21
[    4.636679] ohci1394 0000:00:0d.0: setting latency timer to 64
[    4.688417] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[ea084000-ea0847ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.695794] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[    4.695804] skge 0000:01:04.0: PCI INT A -> Link[APC2] -> GSI 17 (level, high) -> IRQ 17
[    4.695850] skge 1.13 addr 0xe9000000 irq 17 chip Yukon-Lite rev 9
[    4.696222] skge eth1: addr 00:11:d8:82:76:cb
[    4.698027] sata_sil 0000:01:0b.0: version 2.3
[    4.698294] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[    4.698303] sata_sil 0000:01:0b.0: PCI INT A -> Link[APC3] -> GSI 18 (level, high) -> IRQ 18
[    4.699244] scsi0 : sata_sil
[    4.699395] scsi1 : sata_sil
[    4.699434] ata1: SATA max UDMA/100 mmio m512@0xe9004000 tf 0xe9004080 irq 18
[    4.699438] ata2: SATA max UDMA/100 mmio m512@0xe9004000 tf 0xe90040c0 irq 18
[    4.824015] usb 1-2: device not accepting address 2, error -62
[    4.880013] hub 1-0:1.0: unable to enumerate USB device on port 2
[    5.016026] ata1: SATA link down (SStatus 0 SControl 310)
[    5.336024] ata2: SATA link down (SStatus 0 SControl 310)
[    5.344603] pata_amd 0000:00:09.0: version 0.3.10
[    5.344665] pata_amd 0000:00:09.0: setting latency timer to 64
[    5.351346] scsi2 : pata_amd
[    5.353361] scsi3 : pata_amd
[    5.354090] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    5.354094] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    5.616012] usb 3-3: new high speed USB device using ehci_hcd and address 3
[    5.801997] ohci1394: fw-host0: SelfID received outside of bus reset sequence
[    5.821120] usb 3-3: configuration #1 chosen from 1 choice
[    6.044013] usb 3-5: new high speed USB device using ehci_hcd and address 5
[    6.072743] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80000109a0f]
[    6.176574] usb 3-5: configuration #1 chosen from 1 choice
[    6.176992] hub 3-5:1.0: USB hub found
[    6.177429] hub 3-5:1.0: 7 ports detected
[    6.393565] usbcore: registered new interface driver libusual
[    6.400837] Initializing USB Mass Storage driver...
[    6.696012] usb 1-2: new full speed USB device using ohci_hcd and address 4
[    6.907019] usb 1-2: configuration #1 chosen from 1 choice
[    7.212013] usb 2-2: new full speed USB device using ohci_hcd and address 2
[    7.434585] usb 2-2: configuration #1 chosen from 1 choice
[    7.440300] scsi4 : SCSI emulation for USB Mass Storage devices
[    7.440369] usb-storage: device found at 3
[    7.440372] usb-storage: waiting for device to settle before scanning
[    7.528142] usb 3-5.4: new high speed USB device using ehci_hcd and address 6
[    7.637804] usb 3-5.4: configuration #1 chosen from 1 choice
[    7.638524] scsi5 : SCSI emulation for USB Mass Storage devices
[    7.638608] usbcore: registered new interface driver usb-storage
[    7.638612] USB Mass Storage support registered.
[    7.638739] usbcore: registered new interface driver hiddev
[    7.638765] usb-storage: device found at 6
[    7.638768] usb-storage: waiting for device to settle before scanning
[    7.643976] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.1/usb2/2-2/2-2:1.0/input/input2
[    7.656220] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:02.1-2
[    7.665772] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.1/usb2/2-2/2-2:1.1/input/input3
[    7.680256] input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:02.1-2
[    7.680285] usbcore: registered new interface driver usbhid
[    7.680289] usbhid: v2.6:USB HID core driver
[   12.440207] usb-storage: device scan complete
[   12.440822] scsi 4:0:0:0: Direct-Access     PI-192   SATA/USB20 Drive 8.64 PQ: 0 ANSI: 0
[   12.445004] scsi 4:0:0:0: Attached scsi generic sg0 type 0
[   12.454734] Driver 'sd' needs updating - please use bus_type methods
[   12.455425] sd 4:0:0:0: [sda] 156250000 512-byte hardware sectors (80000 MB)
[   12.455930] sd 4:0:0:0: [sda] Write Protect is off
[   12.455934] sd 4:0:0:0: [sda] Mode Sense: 23 00 00 00
[   12.455937] sd 4:0:0:0: [sda] Assuming drive cache: write through
[   12.456678] sd 4:0:0:0: [sda] 156250000 512-byte hardware sectors (80000 MB)
[   12.457296] sd 4:0:0:0: [sda] Write Protect is off
[   12.457300] sd 4:0:0:0: [sda] Mode Sense: 23 00 00 00
[   12.457302] sd 4:0:0:0: [sda] Assuming drive cache: write through
[   12.457308]  sda: sda1 sda2
[   12.497044] sd 4:0:0:0: [sda] Attached SCSI disk
[   12.636172] usb-storage: device scan complete
[   12.636667] scsi 5:0:0:0: Direct-Access     HP       Photosmart D7100 1.00 PQ: 0 ANSI: 2
[   12.641393] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[   12.641534] sd 5:0:0:0: Attached scsi generic sg1 type 0
[   17.801573] kjournald starting.  Commit interval 5 seconds
[   17.801589] EXT3-fs: mounted filesystem with ordered data mode.
[   25.020817] udevd version 124 started
[   25.670105] Linux agpgart interface v0.103
[   25.713859] agpgart: Detected NVIDIA nForce2 chipset
[   25.717702] agpgart-nvidia 0000:00:00.0: AGP aperture is 64M @ 0xe0000000
[   25.860223] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x5000
[   25.860258] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x5500
[   25.963770] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
[   25.976101] ACPI: Power Button (FF) [PWRF]
[   25.976198] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
[   25.992024] ACPI: Power Button (CM) [PWRB]
[   26.525807] parport_pc 00:0c: reported by Plug and Play ACPI
[   26.525866] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   28.297463] usblp0: USB Bidirectional printer dev 6 if 0 alt 0 proto 2 vid 0x03F0 pid 0xC602
[   28.297488] usbcore: registered new interface driver usblp
[   29.021514] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   29.212475] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   29.228949] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   29.973049] nvidia: module license 'NVIDIA' taints kernel.
[   30.255460] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   30.255470] nvidia 0000:03:00.0: PCI INT A -> Link[APC4] -> GSI 19 (level, high) -> IRQ 19
[   30.255879] NVRM: loading NVIDIA UNIX x86 Kernel Module  177.82  Tue Nov  4 13:35:57 PST 2008
[   30.663249] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 20
[   30.663256] Intel ICH 0000:00:06.0: PCI INT A -> Link[APCJ] -> GSI 20 (level, high) -> IRQ 20
[   30.663279] Intel ICH 0000:00:06.0: setting latency timer to 64
[   30.984062] intel8x0_measure_ac97_clock: measured 52821 usecs
[   30.984067] intel8x0: clocking to 48000
[   32.011346] lp0: using parport0 (interrupt-driven).
[   32.589524] EXT3 FS on sda1, internal journal
[   33.165435] type=1505 audit(1234119241.313:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4220
[   33.385955] type=1505 audit(1234119241.533:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4225
[   33.386240] type=1505 audit(1234119241.533:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4225
[   33.440557] type=1505 audit(1234119241.589:5): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=4229
[   33.634169] ip_tables: (C) 2000-2006 Netfilter Core Team
[   34.269590] ACPI: WMI: Mapper loaded
[   35.401265] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   38.037716] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   38.037723] apm: overridden by ACPI.
[   38.310553] ppdev: user-space parallel port driver
[   42.065112] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   42.065119] vboxdrv: Successfully done.
[   42.065122] vboxdrv: Found 1 processor cores.
[   42.066041] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   42.066046] vboxdrv: Successfully loaded version 2.0.4_OSE (interface 0x00090000).
[   42.498565] NET: Registered protocol family 10
[   42.504540] lo: Disabled Privacy Extensions
[   52.084981] Bluetooth: Core ver 2.13
[   52.085528] NET: Registered protocol family 31
[   52.085531] Bluetooth: HCI device and connection manager initialized
[   52.085535] Bluetooth: HCI socket layer initialized
[   52.119470] Bluetooth: L2CAP ver 2.11
[   52.119475] Bluetooth: L2CAP socket layer initialized
[   52.190734] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   52.190739] Bluetooth: BNEP filters: protocol multicast
[   52.268052] Bluetooth: RFCOMM socket layer initialized
[   52.268697] Bluetooth: RFCOMM TTY layer initialized
[   52.268702] Bluetooth: RFCOMM ver 1.10
[   52.370881] Bridge firewalling registered
[   52.446388] Bluetooth: SCO (Voice Link) ver 0.6
[   52.446393] Bluetooth: SCO socket layer initialized
[   53.931938] NET: Registered protocol family 5
[   54.463808] agpgart-nvidia 0000:00:00.0: AGP 3.0 bridge
[   54.463822] agpgart-nvidia 0000:00:00.0: putting AGP V3 device into 8x mode
[   54.463889] nvidia 0000:03:00.0: putting AGP V3 device into 8x mode
[   56.512530] skge eth1: enabling interface
[   56.516417] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   56.997402] NET: Registered protocol family 17
[   66.972017] eth0: no IPv6 routers present
[  158.380224] ppdev0: registered pardevice
[  158.428032] ppdev0: unregistered pardevice
[  159.800678] ppdev0: registered pardevice
[  159.848580] ppdev0: unregistered pardevice
[  159.883741] ppdev0: registered pardevice
[  159.932310] ppdev0: unregistered pardevice
```

---

### Post by kayvortex on 2009-02-08
Yeah, it'd go in the menu.lst file for permanency. Yes, it's a separate command, so you were right to not just tack it on to the end of another one! You could also try adding "acpi=off" too, but this could cause boot problems: again, you could try it.

Reading some of the problems other people seem to have with the SiI 3112 controller, I'm not sure if there's a proper solution; but, again, I'm not knowledgeable enough myself to be able to make any suggestions for solutions anyway (or even fully understand what people are talking about!).

Some interesting (but perhaps not relevent?) reading:
[http://www.gentoo-wiki.info/SATA#SiI_3112_SATA]("http://www.gentoo-wiki.info/SATA#SiI_3112_SATA")
[http://markmail.org/message/osh65nowlzipzjnv]("http://markmail.org/message/osh65nowlzipzjnv")
[http://www.linuxquestions.org/questions/slackware-14/kernel-2.6-and-sata-kernel-panic-507143/]("http://www.linuxquestions.org/questions/slackware-14/kernel-2.6-and-sata-kernel-panic-507143/")

I don't see any obvious problems in dmesg. But that may perhaps be because you won't experience a problem this time around. Try to generate a dmesg output every time you boot so that when your system *does* crash, you can post that up. In the meantime, I guess you'll have to wait and see if your system still crashes or not.

---

### Post by Fazz Munkle on 2009-02-09
Well, so far no freezes. But then again this may be one of those 3 day uptime and then freezes.

Thanks for your help. I really appreciate it. :)

---

