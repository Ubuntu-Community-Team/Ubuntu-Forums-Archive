---
title: "Workstation instable"
date: 2011-07-02
forum: Desktop Environments
---

### Post by 448191 on 2011-07-02
I've been trying to track down this issue for over a week now, and I could really use some help.

It started 6 days ago, when in the morning I found my workstation to be frozen with no video output. I posted [this thread]("http://ubuntuforums.org/showthread.php?t=1790451"), where you can find some log info, but received no replies.

Some info about the system:

 - Intel Xeon W3570 stock speed
 - 24GB Kingston ECC PC-10600 memory
 - Asus P6T6 WS Revolution
 - SAPPHIRE FleX HD 6870 (AMD 6800 Series)
 - LSI 9260 8i, with
 - 4x OCZ Vertex 2 in Raid 0
 - 4x 2TB WD EARS in Raid 5
 - Triple monitor setup, proprietary AMD driver
 - Lucid

Eventually, pressured by a deadline to get the thing working, I put in an old nVidia card of which I knew the fan was failing and reinstalled Lucid. Sure enough, with the hot weather of late, the system froze (at the least convenient moment of course - in the middle of fixing a critical bug in a live website). A reboot after cutting the power left the system unbootable. The beepcodes and P6T6 manual revealed what I suspected: VGA failure.

I put the AMD card back in, removed nvidia drivers and reinstalled the proprietary driver. At boot ubuntu reported fs issues several times, and had me fix them. Eventually, the system seemed stable. CPU temps were acceptable, the northbridge a bit on the hot side. The southbridge, not reported by sensors, felt very hot to the touch. This is where the P6T6 NF200 chip is located that powers the extra PCI buses.

That last bit might be relevant info, as the AMD card is not in the primary PCI slot. The LSI raid card needs to be in that slot, or it will not respond to the keycombo needed to access the card's BIOS. Also I've been told the NF200 has high latency.

I also reset the BIOS, and when I leave the onboard SATA on, it now reports "Not enough space to copy PCI option ROM [00:1F:02]", just before it says "reading NVRAM".

Anyway, it seemed to work, but after a little while Chrome started to freeze on "Waiting for cache..". ~$ ls froze. Apparently the Raid array was inaccessible. After a hard reset, it worked for a while again, this repeated about 3 times, until eventually the issue in the original thread resurfaced: the gnome menu would freeze up and eventually a reboot just gives blank screens at the end of ubuntu boot.

This morning I did a cold boot, it worked for a while again. Eventually the UI froze again, and we're back at blank screens. I am posting this using a bootable USB in low quality VGA mode.

There are several suspects but it seems to me like the southbridge is overheating, or in some way the PCI controller(s) are failing. I would buy a new motherboard but my options for an X58 board that will support ECC memory are really limited. It could also have multiple causes, some other wild guesses:

 - RAID card overheating or defective in some other way

It runs pretty hot, not sure how much it can handle. This would explain the fs access problems, but does not explain why the issue does not occur until at least 1 monitor is a full res using the AMD driver.

 - AMD card overheating

The fan runs fine, the heatpipes get hot but not extremely. Also does not explain fs issues. Seems less likely.

 - Soutbridge overheating or permanently damaged due to overheating

Can't be sure but it seems like under the heatsink of what look likes the southbridge, both a NF200 and ICH10 are housed. As said, it runs really hot. Hotter than the heatpipes on the AMD card. This would explain everything, but I have no concrete evidence other than that it is hot to touch. 

I can just throw money at the issue, buying new hardware, but that might take a long time unless I buy a new MB, Raid card, AND videocard at the same time, which is big chunk of money which will most likely be at least partly wasted. And as I said my choices in motherboards are really limited. I would probably end up with a RS2, which is around 500 EUR I think. The LSI raid card costs about the same. A new eyefinity card would set me back 300 EUR as well. I do not mind replacing one of these if I could be confident that would solve the issue.

I need this workstation so I can work from home and be standby for any issues on live websites. It is critical, so would be eternally grateful for any advice whatsoever anyone can give me.

Thank you in advance,

John

---

### Post by 448191 on 2011-07-02
I forget one other possible issue: SSD(s) defective. They show healthy in the RAID BIOS though.

---

### Post by 448191 on 2011-07-02
Took it apart, dusted it off and put it back together again, switching RAID and GPU slots. Working for now, we'll see if it lasts..

---

### Post by 448191 on 2011-07-02
Ok, so it seems to be stable, but will not allow accelarated graphics... Enabling desktop effects is refused, and glxinfo:


> jkleijn@goliath:~$ glxinfo
name of display: :0.0
Error: couldn't find RGB GLX visual or fbconfig


This my current xorg.conf:

> 
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "0-DFP3"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "2048x1152"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "2048 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-DFP5"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "2048x1152"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "4096 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-DFP4"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "2048x1152"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "Monitor-DFP3" "0-DFP3"
	Option	    "Monitor-DFP5" "0-DFP5"
	Option	    "Monitor-DFP4" "0-DFP4"
	BusID       "PCI:6:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   6144 2048
		Depth     24
	EndSubSection
EndSection


Looks fine to me...

---

### Post by 448191 on 2011-07-02
Reinstalled AMD driver, glx works again. Temps of the card and CPU are stable..

> jkleijn@goliath:~$ aticonfig --adapter=0 --od-gettemperature

Adapter 0 - AMD Radeon HD 6800 Series
            Sensor 0: Temperature - 58.00 C


But, while installing the driver it hung when tried to cancel and ls -la in another console hung as well, for a while at least. On shutdown, the system hung. Cut power and on boot eveything seemed fine.

Can't say I am confident the issue is gone though..

These are messages from that last boot, can't tell if anything is off:
```

Jul  2 17:01:39 goliath kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jul  2 17:01:39 goliath rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="971" x-info="http://www.rsyslog.com"] (re)start
Jul  2 17:01:39 goliath rsyslogd: rsyslogd's groupid changed to 103
Jul  2 17:01:39 goliath rsyslogd: rsyslogd's userid changed to 101
Jul  2 17:01:39 goliath kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul  2 17:01:39 goliath kernel: [    0.000000] Initializing cgroup subsys cpu
Jul  2 17:01:39 goliath kernel: [    0.000000] Linux version 2.6.32-32-generic (buildd@allspice) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #62-Ubuntu SMP Wed Apr 20 21:52:38 UTC 2011 (Ubuntu 2.6.32-32.62-generic 2.6.32.38+drm33.16)
Jul  2 17:01:39 goliath kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-32-generic root=UUID=5b416823-5804-4f21-bafc-50aa31955044 ro quiet splash
Jul  2 17:01:39 goliath kernel: [    0.000000] KERNEL supported cpus:
Jul  2 17:01:39 goliath kernel: [    0.000000]   Intel GenuineIntel
Jul  2 17:01:39 goliath kernel: [    0.000000]   AMD AuthenticAMD
Jul  2 17:01:39 goliath kernel: [    0.000000]   Centaur CentaurHauls
Jul  2 17:01:39 goliath kernel: [    0.000000] BIOS-provided physical RAM map:
Jul  2 17:01:39 goliath kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Jul  2 17:01:39 goliath kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Jul  2 17:01:39 goliath kernel: [    0.000000]  BIOS-e820: 00000000000e4c00 - 0000000000100000 (reserved)
Jul  2 17:01:39 goliath kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf780000 (usable)
Jul  2 17:01:39 goliath kernel: [    0.000000]  BIOS-e820: 00000000bf780000 - 00000000bf798000 (ACPI data)
Jul  2 17:01:39 goliath kernel: [    0.000000]  BIOS-e820: 00000000bf798000 - 00000000bf7dc000 (ACPI NVS)
Jul  2 17:01:39 goliath kernel: [    0.000000]  BIOS-e820: 00000000bf7dc000 - 00000000c0000000 (reserved)
Jul  2 17:01:39 goliath kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jul  2 17:01:39 goliath kernel: [    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
Jul  2 17:01:39 goliath kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000640000000 (usable)
Jul  2 17:01:39 goliath kernel: [    0.000000] DMI 2.5 present.
Jul  2 17:01:39 goliath kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
Jul  2 17:01:39 goliath kernel: [    0.000000] last_pfn = 0x640000 max_arch_pfn = 0x400000000
Jul  2 17:01:39 goliath kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jul  2 17:01:39 goliath kernel: [    0.000000] last_pfn = 0xbf780 max_arch_pfn = 0x400000000
Jul  2 17:01:39 goliath kernel: [    0.000000] Scanning 0 areas for low memory corruption
Jul  2 17:01:39 goliath kernel: [    0.000000] modified physical RAM map:
Jul  2 17:01:39 goliath kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Jul  2 17:01:39 goliath kernel: [    0.000000]  modified: 0000000000010000 - 000000000009f000 (usable)
Jul  2 17:01:39 goliath kernel: [    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
Jul  2 17:01:39 goliath kernel: [    0.000000]  modified: 00000000000e4c00 - 0000000000100000 (reserved)
Jul  2 17:01:39 goliath kernel: [    0.000000]  modified: 0000000000100000 - 00000000bf780000 (usable)
Jul  2 17:01:39 goliath kernel: [    0.000000]  modified: 00000000bf780000 - 00000000bf798000 (ACPI data)
Jul  2 17:01:39 goliath kernel: [    0.000000]  modified: 00000000bf798000 - 00000000bf7dc000 (ACPI NVS)
Jul  2 17:01:39 goliath kernel: [    0.000000]  modified: 00000000bf7dc000 - 00000000c0000000 (reserved)
Jul  2 17:01:39 goliath kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Jul  2 17:01:39 goliath kernel: [    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
Jul  2 17:01:39 goliath kernel: [    0.000000]  modified: 0000000100000000 - 0000000640000000 (usable)
Jul  2 17:01:39 goliath kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000bf780000
Jul  2 17:01:39 goliath kernel: [    0.000000] NX (Execute Disable) protection: active
Jul  2 17:01:39 goliath kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000640000000
Jul  2 17:01:39 goliath kernel: [    0.000000] NX (Execute Disable) protection: active
Jul  2 17:01:39 goliath kernel: [    0.000000] RAMDISK: 377fb000 - 37fef1ec
Jul  2 17:01:39 goliath kernel: [    0.000000] ACPI: RSDP 00000000000fb490 00014 (v00 ACPIAM)
Jul  2 17:01:39 goliath kernel: [    0.000000] ACPI: RSDT 00000000bf780000 00040 (v01 070209 RSDT2041 20090702 MSFT 00000097)
Jul  2 17:01:39 goliath kernel: [    0.000000] ACPI: FACP 00000000bf780200 00084 (v01 070209 FACP2041 20090702 MSFT 00000097)
Jul  2 17:01:39 goliath kernel: [    0.000000] ACPI: DSDT 00000000bf7804b0 0B398 (v01  A1107 A1107001 00000001 INTL 20060113)
Jul  2 17:01:39 goliath kernel: [    0.000000] ACPI: FACS 00000000bf798000 00040
Jul  2 17:01:39 goliath kernel: [    0.000000] ACPI: APIC 00000000bf780390 000D8 (v01 070209 APIC2041 20090702 MSFT 00000097)
Jul  2 17:01:39 goliath kernel: [    0.000000] ACPI: MCFG 00000000bf780470 0003C (v01 070209 OEMMCFG  20090702 MSFT 00000097)
Jul  2 17:01:39 goliath kernel: [    0.000000] ACPI: OEMB 00000000bf798040 00072 (v01 070209 OEMB2041 20090702 MSFT 00000097)
Jul  2 17:01:39 goliath kernel: [    0.000000] ACPI: HPET 00000000bf78f4b0 00038 (v01 070209 OEMHPET  20090702 MSFT 00000097)
Jul  2 17:01:39 goliath kernel: [    0.000000] ACPI: OSFR 00000000bf78f4f0 000B0 (v01 070209 OEMOSFR  20090702 MSFT 00000097)
Jul  2 17:01:39 goliath kernel: [    0.000000] ACPI: SSDT 00000000bf79a940 0249F (v01 DpgPmm    CpuPm 00000012 INTL 20060113)
Jul  2 17:01:39 goliath kernel: [    0.000000] No NUMA configuration found
Jul  2 17:01:39 goliath kernel: [    0.000000] Faking a node at 0000000000000000-0000000640000000
Jul  2 17:01:39 goliath kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000640000000
Jul  2 17:01:39 goliath kernel: [    0.000000]   NODE_DATA [0000000000028000 - 000000000002cfff]
Jul  2 17:01:39 goliath kernel: [    0.000000]   bootmap [0000000000100000 -  00000000001c7fff] pages c8
Jul  2 17:01:39 goliath kernel: [    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0640000000]
Jul  2 17:01:39 goliath kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jul  2 17:01:39 goliath kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Jul  2 17:01:39 goliath kernel: [    0.000000]   #2 [0001000000 - 0001a30a64]    TEXT DATA BSS ==> [0001000000 - 0001a30a64]
Jul  2 17:01:39 goliath kernel: [    0.000000]   #3 [00377fb000 - 0037fef1ec]          RAMDISK ==> [00377fb000 - 0037fef1ec]
Jul  2 17:01:39 goliath kernel: [    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
Jul  2 17:01:39 goliath kernel: [    0.000000]   #5 [0001a31000 - 0001a31298]              BRK ==> [0001a31000 - 0001a31298]
Jul  2 17:01:39 goliath kernel: [    0.000000]   #6 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]
Jul  2 17:01:39 goliath kernel: [    0.000000]   #7 [0000013000 - 0000028000]          PGTABLE ==> [0000013000 - 0000028000]
Jul  2 17:01:39 goliath kernel: [    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
Jul  2 17:01:39 goliath kernel: [    0.000000] Zone PFN ranges:
Jul  2 17:01:39 goliath kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jul  2 17:01:39 goliath kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Jul  2 17:01:39 goliath kernel: [    0.000000]   Normal   0x00100000 -> 0x00640000
Jul  2 17:01:39 goliath kernel: [    0.000000] Movable zone start PFN for each node
Jul  2 17:01:39 goliath kernel: [    0.000000] early_node_map[3] active PFN ranges
Jul  2 17:01:39 goliath kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Jul  2 17:01:39 goliath kernel: [    0.000000]     0: 0x00000100 -> 0x000bf780
Jul  2 17:01:39 goliath kernel: [    0.000000]     0: 0x00100000 -> 0x00640000
Jul  2 17:01:39 goliath kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Jul  2 17:01:39 goliath kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jul  2 17:01:39 goliath kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Jul  2 17:01:39 goliath kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
Jul  2 17:01:39 goliath kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
Jul  2 17:01:39 goliath kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
Jul  2 17:01:39 goliath kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
Jul  2 17:01:39 goliath kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
Jul  2 17:01:39 goliath kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
Jul  2 17:01:39 goliath kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x88] disabled)
Jul  2 17:01:39 goliath kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x89] disabled)
Jul  2 17:01:39 goliath kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x8a] disabled)
Jul  2 17:01:39 goliath kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x8b] disabled)
Jul  2 17:01:39 goliath kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x8c] disabled)
Jul  2 17:01:39 goliath kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x8d] disabled)
Jul  2 17:01:39 goliath kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x8e] disabled)
Jul  2 17:01:39 goliath kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x8f] disabled)
Jul  2 17:01:39 goliath kernel: [    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
Jul  2 17:01:39 goliath kernel: [    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
Jul  2 17:01:39 goliath kernel: [    0.000000] ACPI: IOAPIC (id[0x09] address[0xfec8a000] gsi_base[24])
Jul  2 17:01:39 goliath kernel: [    0.000000] IOAPIC[1]: apic_id 9, version 32, address 0xfec8a000, GSI 24-47
Jul  2 17:01:39 goliath kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul  2 17:01:39 goliath kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jul  2 17:01:39 goliath kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul  2 17:01:39 goliath kernel: [    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
Jul  2 17:01:39 goliath kernel: [    0.000000] SMP: Allowing 16 CPUs, 8 hotplug CPUs
Jul  2 17:01:39 goliath kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jul  2 17:01:39 goliath kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e5000
Jul  2 17:01:39 goliath kernel: [    0.000000] PM: Registered nosave memory: 00000000000e5000 - 0000000000100000
Jul  2 17:01:39 goliath kernel: [    0.000000] PM: Registered nosave memory: 00000000bf780000 - 00000000bf798000
Jul  2 17:01:39 goliath kernel: [    0.000000] PM: Registered nosave memory: 00000000bf798000 - 00000000bf7dc000
Jul  2 17:01:39 goliath kernel: [    0.000000] PM: Registered nosave memory: 00000000bf7dc000 - 00000000c0000000
Jul  2 17:01:39 goliath kernel: [    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000fee00000
Jul  2 17:01:39 goliath kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jul  2 17:01:39 goliath kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffe00000
Jul  2 17:01:39 goliath kernel: [    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
Jul  2 17:01:39 goliath kernel: [    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ee00000)
Jul  2 17:01:39 goliath kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jul  2 17:01:39 goliath kernel: [    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:16 nr_node_ids:1
Jul  2 17:01:39 goliath kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91864 r8192 d22824 u131072
Jul  2 17:01:39 goliath kernel: [    0.000000] pcpu-alloc: s91864 r8192 d22824 u131072 alloc=1*2097152
Jul  2 17:01:39 goliath kernel: [    0.000000] pcpu-alloc: [0] 00 01 02 03 04 05 06 07 08 09 10 11 12 13 14 15 
Jul  2 17:01:39 goliath kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 6199443
Jul  2 17:01:39 goliath kernel: [    0.000000] Policy zone: Normal
Jul  2 17:01:39 goliath kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-32-generic root=UUID=5b416823-5804-4f21-bafc-50aa31955044 ro quiet splash
Jul  2 17:01:39 goliath kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Jul  2 17:01:39 goliath kernel: [    0.000000] Initializing CPU#0
Jul  2 17:01:39 goliath kernel: [    0.000000] Checking aperture...
Jul  2 17:01:39 goliath kernel: [    0.000000] No AGP bridge found
Jul  2 17:01:39 goliath kernel: [    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Jul  2 17:01:39 goliath kernel: [    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
Jul  2 17:01:39 goliath kernel: [    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
Jul  2 17:01:39 goliath kernel: [    0.000000] Memory: 24725736k/26214400k available (5411k kernel code, 1057732k absent, 430932k reserved, 2982k data, 888k init)
Jul  2 17:01:39 goliath kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=16, Nodes=1
Jul  2 17:01:39 goliath kernel: [    0.000000] Hierarchical RCU implementation.
Jul  2 17:01:39 goliath kernel: [    0.000000] NR_IRQS:4352 nr_irqs:944
Jul  2 17:01:39 goliath kernel: [    0.000000] Console: colour VGA+ 80x25
Jul  2 17:01:39 goliath kernel: [    0.000000] console [tty0] enabled
Jul  2 17:01:39 goliath kernel: [    0.000000] allocated 251658240 bytes of page_cgroup
Jul  2 17:01:39 goliath kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jul  2 17:01:39 goliath kernel: [    0.000000] Fast TSC calibration using PIT
Jul  2 17:01:39 goliath kernel: [    0.010000] Detected 3206.965 MHz processor.
Jul  2 17:01:39 goliath kernel: [    0.000004] Calibrating delay loop (skipped), value calculated using timer frequency.. 6413.93 BogoMIPS (lpj=32069650)
Jul  2 17:01:39 goliath kernel: [    0.000016] Security Framework initialized
Jul  2 17:01:39 goliath kernel: [    0.000027] AppArmor: AppArmor initialized
Jul  2 17:01:39 goliath kernel: [    0.001679] Dentry cache hash table entries: 4194304 (order: 13, 33554432 bytes)
Jul  2 17:01:39 goliath kernel: [    0.006615] Inode-cache hash table entries: 2097152 (order: 12, 16777216 bytes)
Jul  2 17:01:39 goliath kernel: [    0.008673] Mount-cache hash table entries: 256
Jul  2 17:01:39 goliath kernel: [    0.008752] Initializing cgroup subsys ns
Jul  2 17:01:39 goliath kernel: [    0.008755] Initializing cgroup subsys cpuacct
Jul  2 17:01:39 goliath kernel: [    0.008757] Initializing cgroup subsys memory
Jul  2 17:01:39 goliath kernel: [    0.008761] Initializing cgroup subsys devices
Jul  2 17:01:39 goliath kernel: [    0.008763] Initializing cgroup subsys freezer
Jul  2 17:01:39 goliath kernel: [    0.008764] Initializing cgroup subsys net_cls
Jul  2 17:01:39 goliath kernel: [    0.008776] CPU: Physical Processor ID: 0
Jul  2 17:01:39 goliath kernel: [    0.008777] CPU: Processor Core ID: 0
Jul  2 17:01:39 goliath kernel: [    0.008779] CPU: L1 I cache: 32K, L1 D cache: 32K
Jul  2 17:01:39 goliath kernel: [    0.008780] CPU: L2 cache: 256K
Jul  2 17:01:39 goliath kernel: [    0.008781] CPU: L3 cache: 8192K
Jul  2 17:01:39 goliath kernel: [    0.008783] CPU 0/0x0 -> Node 0
Jul  2 17:01:39 goliath kernel: [    0.008785] mce: CPU supports 9 MCE banks
Jul  2 17:01:39 goliath kernel: [    0.008793] CPU0: Thermal monitoring enabled (TM1)
Jul  2 17:01:39 goliath kernel: [    0.008795] CPU 0 MCA banks CMCI:2 CMCI:3 CMCI:5 CMCI:6 SHD:8
Jul  2 17:01:39 goliath kernel: [    0.008801] using mwait in idle threads.
Jul  2 17:01:39 goliath kernel: [    0.008802] Performance Events: Nehalem/Corei7 events, Intel PMU driver.
Jul  2 17:01:39 goliath kernel: [    0.008805] ... version:                3
Jul  2 17:01:39 goliath kernel: [    0.008806] ... bit width:              48
Jul  2 17:01:39 goliath kernel: [    0.008807] ... generic registers:      4
Jul  2 17:01:39 goliath kernel: [    0.008808] ... value mask:             0000ffffffffffff
Jul  2 17:01:39 goliath kernel: [    0.008809] ... max period:             000000007fffffff
Jul  2 17:01:39 goliath kernel: [    0.008810] ... fixed-purpose events:   3
Jul  2 17:01:39 goliath kernel: [    0.008811] ... event mask:             000000070000000f
Jul  2 17:01:39 goliath kernel: [    0.010256] ACPI: Core revision 20090903
Jul  2 17:01:39 goliath kernel: [    0.045823] ftrace: converting mcount calls to 0f 1f 44 00 00
Jul  2 17:01:39 goliath kernel: [    0.045829] ftrace: allocating 22476 entries in 89 pages
Jul  2 17:01:39 goliath kernel: [    0.050721] Setting APIC routing to physical flat
Jul  2 17:01:39 goliath kernel: [    0.051139] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jul  2 17:01:39 goliath kernel: [    0.173089] CPU0: Intel(R) Xeon(R) CPU           W3570  @ 3.20GHz stepping 05
Jul  2 17:01:39 goliath kernel: [    0.289312] Booting processor 1 APIC 0x2 ip 0x6000
Jul  2 17:01:39 goliath kernel: [    0.299514] Initializing CPU#1
Jul  2 17:01:39 goliath kernel: [    0.449078] CPU: Physical Processor ID: 0
Jul  2 17:01:39 goliath kernel: [    0.449079] CPU: Processor Core ID: 1
Jul  2 17:01:39 goliath kernel: [    0.449081] CPU: L1 I cache: 32K, L1 D cache: 32K
Jul  2 17:01:39 goliath kernel: [    0.449082] CPU: L2 cache: 256K
Jul  2 17:01:39 goliath kernel: [    0.449083] CPU: L3 cache: 8192K
Jul  2 17:01:39 goliath kernel: [    0.449085] CPU 1/0x2 -> Node 0
Jul  2 17:01:39 goliath kernel: [    0.449093] CPU1: Thermal monitoring enabled (TM1)
Jul  2 17:01:39 goliath kernel: [    0.449095] CPU 1 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8
Jul  2 17:01:39 goliath kernel: [    0.449115] CPU1: Intel(R) Xeon(R) CPU           W3570  @ 3.20GHz stepping 05
Jul  2 17:01:39 goliath kernel: [    0.449121] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Jul  2 17:01:39 goliath kernel: [    0.469173] Booting processor 2 APIC 0x4 ip 0x6000
Jul  2 17:01:39 goliath kernel: [    0.479373] Initializing CPU#2
Jul  2 17:01:39 goliath kernel: [    0.628919] CPU: Physical Processor ID: 0
Jul  2 17:01:39 goliath kernel: [    0.628921] CPU: Processor Core ID: 2
Jul  2 17:01:39 goliath kernel: [    0.628923] CPU: L1 I cache: 32K, L1 D cache: 32K
Jul  2 17:01:39 goliath kernel: [    0.628924] CPU: L2 cache: 256K
Jul  2 17:01:39 goliath kernel: [    0.628924] CPU: L3 cache: 8192K
Jul  2 17:01:39 goliath kernel: [    0.628926] CPU 2/0x4 -> Node 0
Jul  2 17:01:39 goliath kernel: [    0.628935] CPU2: Thermal monitoring enabled (TM1)
Jul  2 17:01:39 goliath kernel: [    0.628937] CPU 2 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8
Jul  2 17:01:39 goliath kernel: [    0.628973] CPU2: Intel(R) Xeon(R) CPU           W3570  @ 3.20GHz stepping 05
Jul  2 17:01:39 goliath kernel: [    0.628979] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
Jul  2 17:01:39 goliath kernel: [    0.649031] Booting processor 3 APIC 0x6 ip 0x6000
Jul  2 17:01:39 goliath kernel: [    0.659232] Initializing CPU#3
Jul  2 17:01:39 goliath kernel: [    0.808759] CPU: Physical Processor ID: 0
Jul  2 17:01:39 goliath kernel: [    0.808760] CPU: Processor Core ID: 3
Jul  2 17:01:39 goliath kernel: [    0.808761] CPU: L1 I cache: 32K, L1 D cache: 32K
Jul  2 17:01:39 goliath kernel: [    0.808762] CPU: L2 cache: 256K
Jul  2 17:01:39 goliath kernel: [    0.808763] CPU: L3 cache: 8192K
Jul  2 17:01:39 goliath kernel: [    0.808764] CPU 3/0x6 -> Node 0
Jul  2 17:01:39 goliath kernel: [    0.808772] CPU3: Thermal monitoring enabled (TM1)
Jul  2 17:01:39 goliath kernel: [    0.808775] CPU 3 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8
Jul  2 17:01:39 goliath kernel: [    0.808828] CPU3: Intel(R) Xeon(R) CPU           W3570  @ 3.20GHz stepping 05
Jul  2 17:01:39 goliath kernel: [    0.808833] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
Jul  2 17:01:39 goliath kernel: [    0.828880] Booting processor 4 APIC 0x1 ip 0x6000
Jul  2 17:01:39 goliath kernel: [    0.839181] Initializing CPU#4
Jul  2 17:01:39 goliath kernel: [    0.988603] CPU: Physical Processor ID: 0
Jul  2 17:01:39 goliath kernel: [    0.988605] CPU: Processor Core ID: 0
Jul  2 17:01:39 goliath kernel: [    0.988607] CPU: L1 I cache: 32K, L1 D cache: 32K
Jul  2 17:01:39 goliath kernel: [    0.988608] CPU: L2 cache: 256K
Jul  2 17:01:39 goliath kernel: [    0.988609] CPU: L3 cache: 8192K
Jul  2 17:01:39 goliath kernel: [    0.988611] CPU 4/0x1 -> Node 0
Jul  2 17:01:39 goliath kernel: [    0.988621] CPU4: Thermal monitoring enabled (TM1)
Jul  2 17:01:39 goliath kernel: [    0.988623] CPU 4 MCA banks SHD:2 SHD:3 SHD:5 SHD:6 SHD:8
Jul  2 17:01:39 goliath kernel: [    0.988685] CPU4: Intel(R) Xeon(R) CPU           W3570  @ 3.20GHz stepping 05
Jul  2 17:01:39 goliath kernel: [    0.988691] checking TSC synchronization [CPU#0 -> CPU#4]: passed.
Jul  2 17:01:39 goliath kernel: [    1.008749] Booting processor 5 APIC 0x3 ip 0x6000
Jul  2 17:01:39 goliath kernel: [    1.018948] Initializing CPU#5
Jul  2 17:01:39 goliath kernel: [    1.168444] CPU: Physical Processor ID: 0
Jul  2 17:01:39 goliath kernel: [    1.168445] CPU: Processor Core ID: 1
Jul  2 17:01:39 goliath kernel: [    1.168447] CPU: L1 I cache: 32K, L1 D cache: 32K
Jul  2 17:01:39 goliath kernel: [    1.168448] CPU: L2 cache: 256K
Jul  2 17:01:39 goliath kernel: [    1.168449] CPU: L3 cache: 8192K
Jul  2 17:01:39 goliath kernel: [    1.168451] CPU 5/0x3 -> Node 0
Jul  2 17:01:39 goliath kernel: [    1.168459] CPU5: Thermal monitoring enabled (TM1)
Jul  2 17:01:39 goliath kernel: [    1.168461] CPU 5 MCA banks SHD:2 SHD:3 SHD:5 SHD:6 SHD:8
Jul  2 17:01:39 goliath kernel: [    1.168490] CPU5: Intel(R) Xeon(R) CPU           W3570  @ 3.20GHz stepping 05
Jul  2 17:01:39 goliath kernel: [    1.168496] checking TSC synchronization [CPU#0 -> CPU#5]: passed.
Jul  2 17:01:39 goliath kernel: [    1.188550] Booting processor 6 APIC 0x5 ip 0x6000
Jul  2 17:01:39 goliath kernel: [    1.198750] Initializing CPU#6
Jul  2 17:01:39 goliath kernel: [    1.348283] CPU: Physical Processor ID: 0
Jul  2 17:01:39 goliath kernel: [    1.348284] CPU: Processor Core ID: 2
Jul  2 17:01:39 goliath kernel: [    1.348286] CPU: L1 I cache: 32K, L1 D cache: 32K
Jul  2 17:01:39 goliath kernel: [    1.348287] CPU: L2 cache: 256K
Jul  2 17:01:39 goliath kernel: [    1.348287] CPU: L3 cache: 8192K
Jul  2 17:01:39 goliath kernel: [    1.348289] CPU 6/0x5 -> Node 0
Jul  2 17:01:39 goliath kernel: [    1.348297] CPU6: Thermal monitoring enabled (TM1)
Jul  2 17:01:39 goliath kernel: [    1.348299] CPU 6 MCA banks SHD:2 SHD:3 SHD:5 SHD:6 SHD:8
Jul  2 17:01:39 goliath kernel: [    1.348361] CPU6: Intel(R) Xeon(R) CPU           W3570  @ 3.20GHz stepping 05
Jul  2 17:01:39 goliath kernel: [    1.348366] checking TSC synchronization [CPU#0 -> CPU#6]: passed.
Jul  2 17:01:39 goliath kernel: [    1.368424] Booting processor 7 APIC 0x7 ip 0x6000
Jul  2 17:01:39 goliath kernel: [    1.378625] Initializing CPU#7
Jul  2 17:01:39 goliath kernel: [    1.528125] CPU: Physical Processor ID: 0
Jul  2 17:01:39 goliath kernel: [    1.528126] CPU: Processor Core ID: 3
Jul  2 17:01:39 goliath kernel: [    1.528127] CPU: L1 I cache: 32K, L1 D cache: 32K
Jul  2 17:01:39 goliath kernel: [    1.528128] CPU: L2 cache: 256K
Jul  2 17:01:39 goliath kernel: [    1.528129] CPU: L3 cache: 8192K
Jul  2 17:01:39 goliath kernel: [    1.528130] CPU 7/0x7 -> Node 0
Jul  2 17:01:39 goliath kernel: [    1.528139] CPU7: Thermal monitoring enabled (TM1)
Jul  2 17:01:39 goliath kernel: [    1.528141] CPU 7 MCA banks SHD:2 SHD:3 SHD:5 SHD:6 SHD:8
Jul  2 17:01:39 goliath kernel: [    1.528236] CPU7: Intel(R) Xeon(R) CPU           W3570  @ 3.20GHz stepping 05
Jul  2 17:01:39 goliath kernel: [    1.528241] checking TSC synchronization [CPU#0 -> CPU#7]: passed.
Jul  2 17:01:39 goliath kernel: [    1.548243] Brought up 8 CPUs
Jul  2 17:01:39 goliath kernel: [    1.548244] Total of 8 processors activated (51315.36 BogoMIPS).
Jul  2 17:01:39 goliath kernel: [    1.551913] devtmpfs: initialized
Jul  2 17:01:39 goliath kernel: [    1.552112] regulator: core version 0.5
Jul  2 17:01:39 goliath kernel: [    1.552132] Time: 15:01:37  Date: 07/02/11
Jul  2 17:01:39 goliath kernel: [    1.552160] NET: Registered protocol family 16
Jul  2 17:01:39 goliath kernel: [    1.552218] Trying to unpack rootfs image as initramfs...
Jul  2 17:01:39 goliath kernel: [    1.552228] ACPI: bus type pci registered
Jul  2 17:01:39 goliath kernel: [    1.552275] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Jul  2 17:01:39 goliath kernel: [    1.552276] PCI: Not using MMCONFIG.
Jul  2 17:01:39 goliath kernel: [    1.552277] PCI: Using configuration type 1 for base access
Jul  2 17:01:39 goliath kernel: [    1.552788] bio: create slab <bio-0> at 0
Jul  2 17:01:39 goliath kernel: [    1.555106] ACPI: Executed 1 blocks of module-level executable AML code
Jul  2 17:01:39 goliath kernel: [    1.588338] ACPI: Interpreter enabled
Jul  2 17:01:39 goliath kernel: [    1.588342] ACPI: (supports S0 S1 S3 S4 S5)
Jul  2 17:01:39 goliath kernel: [    1.588359] ACPI: Using IOAPIC for interrupt routing
Jul  2 17:01:39 goliath kernel: [    1.588402] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Jul  2 17:01:39 goliath kernel: [    1.589862] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
Jul  2 17:01:39 goliath kernel: [    1.594289] PCI: Using MMCONFIG at e0000000 - efffffff
Jul  2 17:01:39 goliath kernel: [    1.600469] ACPI: No dock devices found.
Jul  2 17:01:39 goliath kernel: [    1.600580] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul  2 17:01:39 goliath kernel: [    1.600638] pci 0000:00:00.0: PME# supported from D0 D3hot D3cold
Jul  2 17:01:39 goliath kernel: [    1.600640] pci 0000:00:00.0: PME# disabled
Jul  2 17:01:39 goliath kernel: [    1.600688] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Jul  2 17:01:39 goliath kernel: [    1.600690] pci 0000:00:01.0: PME# disabled
Jul  2 17:01:39 goliath kernel: [    1.600740] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
Jul  2 17:01:39 goliath kernel: [    1.600742] pci 0000:00:03.0: PME# disabled
Jul  2 17:01:39 goliath kernel: [    1.600791] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
Jul  2 17:01:39 goliath kernel: [    1.600793] pci 0000:00:07.0: PME# disabled
Jul  2 17:01:39 goliath kernel: [    1.601188] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Jul  2 17:01:39 goliath kernel: [    1.601191] pci 0000:00:1a.7: PME# disabled
Jul  2 17:01:39 goliath kernel: [    1.601256] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jul  2 17:01:39 goliath kernel: [    1.601259] pci 0000:00:1b.0: PME# disabled
Jul  2 17:01:39 goliath kernel: [    1.601308] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jul  2 17:01:39 goliath kernel: [    1.601311] pci 0000:00:1c.0: PME# disabled
Jul  2 17:01:39 goliath kernel: [    1.601362] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Jul  2 17:01:39 goliath kernel: [    1.601364] pci 0000:00:1c.1: PME# disabled
Jul  2 17:01:39 goliath kernel: [    1.601415] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Jul  2 17:01:39 goliath kernel: [    1.601418] pci 0000:00:1c.2: PME# disabled
Jul  2 17:01:39 goliath kernel: [    1.601468] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Jul  2 17:01:39 goliath kernel: [    1.601471] pci 0000:00:1c.3: PME# disabled
Jul  2 17:01:39 goliath kernel: [    1.601734] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Jul  2 17:01:39 goliath kernel: [    1.601737] pci 0000:00:1d.7: PME# disabled
Jul  2 17:01:39 goliath kernel: [    1.601842] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0294 (mask 0003)
Jul  2 17:01:39 goliath kernel: [    1.601846] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 4700 (mask 001f)
Jul  2 17:01:39 goliath kernel: [    1.602090] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
Jul  2 17:01:39 goliath kernel: [    1.602092] pci 0000:02:00.0: PME# disabled
Jul  2 17:01:39 goliath kernel: [    1.602151] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
Jul  2 17:01:39 goliath kernel: [    1.602154] pci 0000:03:00.0: PME# disabled
Jul  2 17:01:39 goliath kernel: [    1.602192] pci 0000:03:02.0: PME# supported from D0 D3hot D3cold
Jul  2 17:01:39 goliath kernel: [    1.602194] pci 0000:03:02.0: PME# disabled
Jul  2 17:01:39 goliath kernel: [    1.602683] pci 0000:09:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul  2 17:01:39 goliath kernel: [    1.602687] pci 0000:09:00.0: PME# disabled
Jul  2 17:01:39 goliath kernel: [    1.602850] pci 0000:08:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul  2 17:01:39 goliath kernel: [    1.602854] pci 0000:08:00.0: PME# disabled
Jul  2 17:01:39 goliath kernel: [    1.603015] pci 0000:07:00.0: PME# supported from D0 D1 D3hot
Jul  2 17:01:39 goliath kernel: [    1.603019] pci 0000:07:00.0: PME# disabled
Jul  2 17:01:39 goliath kernel: [    1.603100] pci 0000:00:1e.0: transparent bridge
Jul  2 17:01:39 goliath kernel: [    1.626347] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 11 12 14 *15)
Jul  2 17:01:39 goliath kernel: [    1.626436] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
Jul  2 17:01:39 goliath kernel: [    1.626521] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12 14 15)
Jul  2 17:01:39 goliath kernel: [    1.626607] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 *10 11 12 14 15)
Jul  2 17:01:39 goliath kernel: [    1.626693] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 *14 15)
Jul  2 17:01:39 goliath kernel: [    1.626779] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 6 7 10 11 12 14 15)
Jul  2 17:01:39 goliath kernel: [    1.626866] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 6 7 *10 11 12 14 15)
Jul  2 17:01:39 goliath kernel: [    1.626952] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 6 7 10 *11 12 14 15)
Jul  2 17:01:39 goliath kernel: [    1.627033] vgaarb: device added: PCI:0000:06:00.0,decodes=io+mem,owns=io+mem,locks=none
Jul  2 17:01:39 goliath kernel: [    1.627035] vgaarb: loaded
Jul  2 17:01:39 goliath kernel: [    1.627099] SCSI subsystem initialized
Jul  2 17:01:39 goliath kernel: [    1.627244] usbcore: registered new interface driver usbfs
Jul  2 17:01:39 goliath kernel: [    1.627253] usbcore: registered new interface driver hub
Jul  2 17:01:39 goliath kernel: [    1.627267] usbcore: registered new device driver usb
Jul  2 17:01:39 goliath kernel: [    1.627348] ACPI: WMI: Mapper loaded
Jul  2 17:01:39 goliath kernel: [    1.627349] PCI: Using ACPI for IRQ routing
Jul  2 17:01:39 goliath kernel: [    1.627480] NetLabel: Initializing
Jul  2 17:01:39 goliath kernel: [    1.627481] NetLabel:  domain hash size = 128
Jul  2 17:01:39 goliath kernel: [    1.627482] NetLabel:  protocols = UNLABELED CIPSOv4
Jul  2 17:01:39 goliath kernel: [    1.627489] NetLabel:  unlabeled traffic allowed by default
Jul  2 17:01:39 goliath kernel: [    1.627514] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
Jul  2 17:01:39 goliath kernel: [    1.627518] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Jul  2 17:01:39 goliath kernel: [    1.627520] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
Jul  2 17:01:39 goliath kernel: [    1.658162] Switching to clocksource tsc
Jul  2 17:01:39 goliath kernel: [    1.659332] AppArmor: AppArmor Filesystem Enabled
Jul  2 17:01:39 goliath kernel: [    1.659341] pnp: PnP ACPI init
Jul  2 17:01:39 goliath kernel: [    1.659351] ACPI: bus type pnp registered
Jul  2 17:01:39 goliath kernel: [    1.661066] pnp: PnP ACPI: found 14 devices
Jul  2 17:01:39 goliath kernel: [    1.661067] ACPI: ACPI bus type pnp unregistered
Jul  2 17:01:39 goliath kernel: [    1.661074] system 00:01: iomem range 0xfbf00000-0xfbffffff has been reserved
Jul  2 17:01:39 goliath kernel: [    1.661076] system 00:01: iomem range 0xfc000000-0xfcffffff has been reserved
Jul  2 17:01:39 goliath kernel: [    1.661077] system 00:01: iomem range 0xfd000000-0xfdffffff has been reserved
Jul  2 17:01:39 goliath kernel: [    1.661079] system 00:01: iomem range 0xfe000000-0xfebfffff has been reserved
Jul  2 17:01:39 goliath kernel: [    1.661080] system 00:01: iomem range 0xfec8a000-0xfec8afff could not be reserved
Jul  2 17:01:39 goliath kernel: [    1.661082] system 00:01: iomem range 0xfed10000-0xfed10fff has been reserved
Jul  2 17:01:39 goliath kernel: [    1.661086] system 00:06: ioport range 0x290-0x29f has been reserved
Jul  2 17:01:39 goliath kernel: [    1.661089] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
Jul  2 17:01:39 goliath kernel: [    1.661091] system 00:07: ioport range 0x800-0x87f has been reserved
Jul  2 17:01:39 goliath kernel: [    1.661092] system 00:07: ioport range 0x500-0x57f has been reserved
Jul  2 17:01:39 goliath kernel: [    1.661094] system 00:07: iomem range 0xfed1c000-0xfed1ffff has been reserved
Jul  2 17:01:39 goliath kernel: [    1.661095] system 00:07: iomem range 0xfed20000-0xfed3ffff has been reserved
Jul  2 17:01:39 goliath kernel: [    1.661097] system 00:07: iomem range 0xfed40000-0xfed8ffff has been reserved
Jul  2 17:01:39 goliath kernel: [    1.661100] system 00:0a: iomem range 0xffc00000-0xffdfffff has been reserved
Jul  2 17:01:39 goliath kernel: [    1.661103] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
Jul  2 17:01:39 goliath kernel: [    1.661105] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
Jul  2 17:01:39 goliath kernel: [    1.661107] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
Jul  2 17:01:39 goliath kernel: [    1.661110] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
Jul  2 17:01:39 goliath kernel: [    1.661112] system 00:0d: iomem range 0xc0000-0xcffff has been reserved
Jul  2 17:01:39 goliath kernel: [    1.661113] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
Jul  2 17:01:39 goliath kernel: [    1.661115] system 00:0d: iomem range 0x100000-0xbfffffff could not be reserved
Jul  2 17:01:39 goliath kernel: [    1.661116] system 00:0d: iomem range 0xfed90000-0xffffffff could not be reserved
Jul  2 17:01:39 goliath kernel: [    1.665788] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Jul  2 17:01:39 goliath kernel: [    1.665789] pci 0000:00:01.0:   IO window: disabled
Jul  2 17:01:39 goliath kernel: [    1.665792] pci 0000:00:01.0:   MEM window: disabled
Jul  2 17:01:39 goliath kernel: [    1.665794] pci 0000:00:01.0:   PREFETCH window: disabled
Jul  2 17:01:39 goliath kernel: [    1.665797] pci 0000:03:00.0: PCI bridge, secondary bus 0000:04
Jul  2 17:01:39 goliath kernel: [    1.665798] pci 0000:03:00.0:   IO window: disabled
Jul  2 17:01:39 goliath kernel: [    1.665801] pci 0000:03:00.0:   MEM window: disabled
Jul  2 17:01:39 goliath kernel: [    1.665803] pci 0000:03:00.0:   PREFETCH window: disabled
Jul  2 17:01:39 goliath kernel: [    1.665807] pci 0000:03:02.0: PCI bridge, secondary bus 0000:05
Jul  2 17:01:39 goliath kernel: [    1.665809] pci 0000:03:02.0:   IO window: 0xa000-0xafff
Jul  2 17:01:39 goliath kernel: [    1.665812] pci 0000:03:02.0:   MEM window: 0xfba00000-0xfbafffff
Jul  2 17:01:39 goliath kernel: [    1.665814] pci 0000:03:02.0:   PREFETCH window: disabled
Jul  2 17:01:39 goliath kernel: [    1.665818] pci 0000:02:00.0: PCI bridge, secondary bus 0000:03
Jul  2 17:01:39 goliath kernel: [    1.665819] pci 0000:02:00.0:   IO window: 0xa000-0xafff
Jul  2 17:01:39 goliath kernel: [    1.665822] pci 0000:02:00.0:   MEM window: 0xfba00000-0xfbafffff
Jul  2 17:01:39 goliath kernel: [    1.665825] pci 0000:02:00.0:   PREFETCH window: disabled
Jul  2 17:01:39 goliath kernel: [    1.665828] pci 0000:00:03.0: PCI bridge, secondary bus 0000:02
Jul  2 17:01:39 goliath kernel: [    1.665830] pci 0000:00:03.0:   IO window: 0xa000-0xafff
Jul  2 17:01:39 goliath kernel: [    1.665833] pci 0000:00:03.0:   MEM window: 0xfba00000-0xfbafffff
Jul  2 17:01:39 goliath kernel: [    1.665835] pci 0000:00:03.0:   PREFETCH window: disabled
Jul  2 17:01:39 goliath kernel: [    1.665838] pci 0000:00:07.0: PCI bridge, secondary bus 0000:06
Jul  2 17:01:39 goliath kernel: [    1.665840] pci 0000:00:07.0:   IO window: 0xb000-0xbfff
Jul  2 17:01:39 goliath kernel: [    1.665843] pci 0000:00:07.0:   MEM window: 0xfbb00000-0xfbbfffff
Jul  2 17:01:39 goliath kernel: [    1.665845] pci 0000:00:07.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
Jul  2 17:01:39 goliath kernel: [    1.665849] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0a
Jul  2 17:01:39 goliath kernel: [    1.665851] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
Jul  2 17:01:39 goliath kernel: [    1.665854] pci 0000:00:1c.0:   MEM window: 0xc0000000-0xc03fffff
Jul  2 17:01:39 goliath kernel: [    1.665857] pci 0000:00:1c.0:   PREFETCH window: 0x000000faf00000-0x000000faffffff
Jul  2 17:01:39 goliath kernel: [    1.665861] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:09
Jul  2 17:01:39 goliath kernel: [    1.665863] pci 0000:00:1c.1:   IO window: 0xe000-0xefff
Jul  2 17:01:39 goliath kernel: [    1.665866] pci 0000:00:1c.1:   MEM window: 0xfbe00000-0xfbefffff
Jul  2 17:01:39 goliath kernel: [    1.665869] pci 0000:00:1c.1:   PREFETCH window: 0x000000fae00000-0x000000faefffff
Jul  2 17:01:39 goliath kernel: [    1.665873] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:08
Jul  2 17:01:39 goliath kernel: [    1.665875] pci 0000:00:1c.2:   IO window: 0xd000-0xdfff
Jul  2 17:01:39 goliath kernel: [    1.665878] pci 0000:00:1c.2:   MEM window: 0xfbd00000-0xfbdfffff
Jul  2 17:01:39 goliath kernel: [    1.665881] pci 0000:00:1c.2:   PREFETCH window: 0x000000fad00000-0x000000fadfffff
Jul  2 17:01:39 goliath kernel: [    1.665885] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:07
Jul  2 17:01:39 goliath kernel: [    1.665887] pci 0000:00:1c.3:   IO window: 0xc000-0xcfff
Jul  2 17:01:39 goliath kernel: [    1.665890] pci 0000:00:1c.3:   MEM window: 0xfbc00000-0xfbcfffff
Jul  2 17:01:39 goliath kernel: [    1.665893] pci 0000:00:1c.3:   PREFETCH window: 0x000000c0400000-0x000000c05fffff
Jul  2 17:01:39 goliath kernel: [    1.665897] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:0b
Jul  2 17:01:39 goliath kernel: [    1.665898] pci 0000:00:1e.0:   IO window: disabled
Jul  2 17:01:39 goliath kernel: [    1.665901] pci 0000:00:1e.0:   MEM window: disabled
Jul  2 17:01:39 goliath kernel: [    1.665903] pci 0000:00:1e.0:   PREFETCH window: disabled
Jul  2 17:01:39 goliath kernel: [    1.665945] pci 0000:00:1c.0: enabling device (0106 -> 0107)
Jul  2 17:01:39 goliath kernel: [    1.665954] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jul  2 17:01:39 goliath kernel: [    1.665965] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Jul  2 17:01:39 goliath kernel: [    1.665976] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jul  2 17:01:39 goliath kernel: [    1.665986] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Jul  2 17:01:39 goliath kernel: [    1.666050] NET: Registered protocol family 2
Jul  2 17:01:39 goliath kernel: [    1.666307] IP route cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jul  2 17:01:39 goliath kernel: [    1.667158] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Jul  2 17:01:39 goliath kernel: [    1.668215] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jul  2 17:01:39 goliath kernel: [    1.668337] TCP: Hash tables configured (established 524288 bind 65536)
Jul  2 17:01:39 goliath kernel: [    1.668339] TCP reno registered
Jul  2 17:01:39 goliath kernel: [    1.668414] NET: Registered protocol family 1
Jul  2 17:01:39 goliath kernel: [    1.668881] Scanning for low memory corruption every 60 seconds
Jul  2 17:01:39 goliath kernel: [    1.668955] audit: initializing netlink socket (disabled)
Jul  2 17:01:39 goliath kernel: [    1.668960] type=2000 audit(1309618897.469:1): initialized
Jul  2 17:01:39 goliath kernel: [    1.676238] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jul  2 17:01:39 goliath kernel: [    1.677116] VFS: Disk quotas dquot_6.5.2
Jul  2 17:01:39 goliath kernel: [    1.677150] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jul  2 17:01:39 goliath kernel: [    1.677518] fuse init (API version 7.13)
Jul  2 17:01:39 goliath kernel: [    1.677568] msgmni has been set to 32768
Jul  2 17:01:39 goliath kernel: [    1.677738] alg: No test for stdrng (krng)
Jul  2 17:01:39 goliath kernel: [    1.677770] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jul  2 17:01:39 goliath kernel: [    1.677772] io scheduler noop registered
Jul  2 17:01:39 goliath kernel: [    1.677773] io scheduler anticipatory registered
Jul  2 17:01:39 goliath kernel: [    1.677774] io scheduler deadline registered
Jul  2 17:01:39 goliath kernel: [    1.677795] io scheduler cfq registered (default)
Jul  2 17:01:39 goliath kernel: [    1.678575] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul  2 17:01:39 goliath kernel: [    1.678656] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jul  2 17:01:39 goliath kernel: [    1.678712] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Jul  2 17:01:39 goliath kernel: [    1.678714] ACPI: Power Button [PWRB]
Jul  2 17:01:39 goliath kernel: [    1.678738] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Jul  2 17:01:39 goliath kernel: [    1.678740] ACPI: Power Button [PWRF]
Jul  2 17:01:39 goliath kernel: [    1.679363] ACPI: SSDT 00000000bf7980c0 0050B (v01 DpgPmm  P001Ist 00000011 INTL 20060113)
Jul  2 17:01:39 goliath kernel: [    1.679572] processor LNXCPU:00: registered as cooling_device0
Jul  2 17:01:39 goliath kernel: [    1.679925] ACPI: SSDT 00000000bf7985d0 0050B (v01 DpgPmm  P002Ist 00000012 INTL 20060113)
Jul  2 17:01:39 goliath kernel: [    1.680122] processor LNXCPU:01: registered as cooling_device1
Jul  2 17:01:39 goliath kernel: [    1.680470] ACPI: SSDT 00000000bf798ae0 0050B (v01 DpgPmm  P003Ist 00000012 INTL 20060113)
Jul  2 17:01:39 goliath kernel: [    1.680666] processor LNXCPU:02: registered as cooling_device2
Jul  2 17:01:39 goliath kernel: [    1.681038] ACPI: SSDT 00000000bf798ff0 0050B (v01 DpgPmm  P004Ist 00000012 INTL 20060113)
Jul  2 17:01:39 goliath kernel: [    1.681235] processor LNXCPU:03: registered as cooling_device3
Jul  2 17:01:39 goliath kernel: [    1.681593] ACPI: SSDT 00000000bf799500 0050B (v01 DpgPmm  P005Ist 00000012 INTL 20060113)
Jul  2 17:01:39 goliath kernel: [    1.681791] processor LNXCPU:04: registered as cooling_device4
Jul  2 17:01:39 goliath kernel: [    1.682142] ACPI: SSDT 00000000bf799a10 0050B (v01 DpgPmm  P006Ist 00000012 INTL 20060113)
Jul  2 17:01:39 goliath kernel: [    1.682344] processor LNXCPU:05: registered as cooling_device5
Jul  2 17:01:39 goliath kernel: [    1.682707] ACPI: SSDT 00000000bf799f20 0050B (v01 DpgPmm  P007Ist 00000012 INTL 20060113)
Jul  2 17:01:39 goliath kernel: [    1.682904] processor LNXCPU:06: registered as cooling_device6
Jul  2 17:01:39 goliath kernel: [    1.683260] ACPI: SSDT 00000000bf79a430 0050B (v01 DpgPmm  P008Ist 00000012 INTL 20060113)
Jul  2 17:01:39 goliath kernel: [    1.683459] processor LNXCPU:07: registered as cooling_device7
Jul  2 17:01:39 goliath kernel: [    1.685790] Linux agpgart interface v0.103
Jul  2 17:01:39 goliath kernel: [    1.685808] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Jul  2 17:01:39 goliath kernel: [    1.685890] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul  2 17:01:39 goliath kernel: [    1.686584] brd: module loaded
Jul  2 17:01:39 goliath kernel: [    1.686844] loop: module loaded
Jul  2 17:01:39 goliath kernel: [    1.686887] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Jul  2 17:01:39 goliath kernel: [    1.686946] ata_piix 0000:00:1f.2: PCI INT B -> GSI 20 (level, low) -> IRQ 20
Jul  2 17:01:39 goliath kernel: [    1.686949] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Jul  2 17:01:39 goliath kernel: [    1.687011] scsi0 : ata_piix
Jul  2 17:01:39 goliath kernel: [    1.687058] scsi1 : ata_piix
Jul  2 17:01:39 goliath kernel: [    1.687857] ata1: SATA max UDMA/133 cmd 0x8000 ctl 0x7c00 bmdma 0x7480 irq 20
Jul  2 17:01:39 goliath kernel: [    1.687861] ata2: SATA max UDMA/133 cmd 0x7880 ctl 0x7800 bmdma 0x7488 irq 20
Jul  2 17:01:39 goliath kernel: [    1.687876] ata_piix 0000:00:1f.5: PCI INT B -> GSI 20 (level, low) -> IRQ 20
Jul  2 17:01:39 goliath kernel: [    1.687880] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
Jul  2 17:01:39 goliath kernel: [    1.687927] scsi2 : ata_piix
Jul  2 17:01:39 goliath kernel: [    1.687956] scsi3 : ata_piix
Jul  2 17:01:39 goliath kernel: [    1.688735] ata3: SATA max UDMA/133 cmd 0x9000 ctl 0x8c00 bmdma 0x8480 irq 20
Jul  2 17:01:39 goliath kernel: [    1.688738] ata4: SATA max UDMA/133 cmd 0x8880 ctl 0x8800 bmdma 0x8488 irq 20
Jul  2 17:01:39 goliath kernel: [    1.688784] pata_acpi 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jul  2 17:01:39 goliath kernel: [    1.688807] pata_acpi 0000:07:00.0: PCI INT A disabled
Jul  2 17:01:39 goliath kernel: [    1.688953] Fixed MDIO Bus: probed
Jul  2 17:01:39 goliath kernel: [    1.688970] PPP generic driver version 2.4.2
Jul  2 17:01:39 goliath kernel: [    1.688991] tun: Universal TUN/TAP device driver, 1.6
Jul  2 17:01:39 goliath kernel: [    1.688992] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jul  2 17:01:39 goliath kernel: [    1.689037] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jul  2 17:01:39 goliath kernel: [    1.689048] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jul  2 17:01:39 goliath kernel: [    1.689062] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Jul  2 17:01:39 goliath kernel: [    1.689079] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Jul  2 17:01:39 goliath kernel: [    1.689101] ehci_hcd 0000:00:1a.7: debug port 1
Jul  2 17:01:39 goliath kernel: [    1.691564] Freeing initrd memory: 8144k freed
Jul  2 17:01:39 goliath kernel: [    1.692997] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfb9ff000
Jul  2 17:01:39 goliath kernel: [    1.708226] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Jul  2 17:01:39 goliath kernel: [    1.708325] usb usb1: configuration #1 chosen from 1 choice
Jul  2 17:01:39 goliath kernel: [    1.708341] hub 1-0:1.0: USB hub found
Jul  2 17:01:39 goliath kernel: [    1.708346] hub 1-0:1.0: 6 ports detected
Jul  2 17:01:39 goliath kernel: [    1.708394] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jul  2 17:01:39 goliath kernel: [    1.708411] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jul  2 17:01:39 goliath kernel: [    1.708430] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Jul  2 17:01:39 goliath kernel: [    1.708453] ehci_hcd 0000:00:1d.7: debug port 1
Jul  2 17:01:39 goliath kernel: [    1.712351] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfb9fe000
Jul  2 17:01:39 goliath kernel: [    1.728208] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Jul  2 17:01:39 goliath kernel: [    1.728291] usb usb2: configuration #1 chosen from 1 choice
Jul  2 17:01:39 goliath kernel: [    1.728304] hub 2-0:1.0: USB hub found
Jul  2 17:01:39 goliath kernel: [    1.728307] hub 2-0:1.0: 6 ports detected
Jul  2 17:01:39 goliath kernel: [    1.728344] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jul  2 17:01:39 goliath kernel: [    1.728353] uhci_hcd: USB Universal Host Controller Interface driver
Jul  2 17:01:39 goliath kernel: [    1.728375] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul  2 17:01:39 goliath kernel: [    1.728382] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Jul  2 17:01:39 goliath kernel: [    1.728400] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Jul  2 17:01:39 goliath kernel: [    1.728425] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00009800
Jul  2 17:01:39 goliath kernel: [    1.728474] usb usb3: configuration #1 chosen from 1 choice
Jul  2 17:01:39 goliath kernel: [    1.728487] hub 3-0:1.0: USB hub found
Jul  2 17:01:39 goliath kernel: [    1.728490] hub 3-0:1.0: 2 ports detected
Jul  2 17:01:39 goliath kernel: [    1.728522] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Jul  2 17:01:39 goliath kernel: [    1.728527] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Jul  2 17:01:39 goliath kernel: [    1.728544] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Jul  2 17:01:39 goliath kernel: [    1.728569] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00009880
Jul  2 17:01:39 goliath kernel: [    1.728615] usb usb4: configuration #1 chosen from 1 choice
Jul  2 17:01:39 goliath kernel: [    1.728628] hub 4-0:1.0: USB hub found
Jul  2 17:01:39 goliath kernel: [    1.728631] hub 4-0:1.0: 2 ports detected
Jul  2 17:01:39 goliath kernel: [    1.728656] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Jul  2 17:01:39 goliath kernel: [    1.728662] uhci_hcd 0000:00:1a.2: UHCI Host Controller
Jul  2 17:01:39 goliath kernel: [    1.728681] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
Jul  2 17:01:39 goliath kernel: [    1.728705] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00009c00
Jul  2 17:01:39 goliath kernel: [    1.728751] usb usb5: configuration #1 chosen from 1 choice
Jul  2 17:01:39 goliath kernel: [    1.728766] hub 5-0:1.0: USB hub found
Jul  2 17:01:39 goliath kernel: [    1.728768] hub 5-0:1.0: 2 ports detected
Jul  2 17:01:39 goliath kernel: [    1.728800] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jul  2 17:01:39 goliath kernel: [    1.728805] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jul  2 17:01:39 goliath kernel: [    1.728822] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
Jul  2 17:01:39 goliath kernel: [    1.728841] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00009080
Jul  2 17:01:39 goliath kernel: [    1.728887] usb usb6: configuration #1 chosen from 1 choice
Jul  2 17:01:39 goliath kernel: [    1.728901] hub 6-0:1.0: USB hub found
Jul  2 17:01:39 goliath kernel: [    1.728904] hub 6-0:1.0: 2 ports detected
Jul  2 17:01:39 goliath kernel: [    1.728929] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jul  2 17:01:39 goliath kernel: [    1.728934] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jul  2 17:01:39 goliath kernel: [    1.728951] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
Jul  2 17:01:39 goliath kernel: [    1.728970] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00009400
Jul  2 17:01:39 goliath kernel: [    1.729018] usb usb7: configuration #1 chosen from 1 choice
Jul  2 17:01:39 goliath kernel: [    1.729031] hub 7-0:1.0: USB hub found
Jul  2 17:01:39 goliath kernel: [    1.729035] hub 7-0:1.0: 2 ports detected
Jul  2 17:01:39 goliath kernel: [    1.729061] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jul  2 17:01:39 goliath kernel: [    1.729066] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jul  2 17:01:39 goliath kernel: [    1.729085] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
Jul  2 17:01:39 goliath kernel: [    1.729106] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00009480
Jul  2 17:01:39 goliath kernel: [    1.729152] usb usb8: configuration #1 chosen from 1 choice
Jul  2 17:01:39 goliath kernel: [    1.729164] hub 8-0:1.0: USB hub found
Jul  2 17:01:39 goliath kernel: [    1.729167] hub 8-0:1.0: 2 ports detected
Jul  2 17:01:39 goliath kernel: [    1.729221] PNP: No PS/2 controller found. Probing ports directly.
Jul  2 17:01:39 goliath kernel: [    1.731748] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul  2 17:01:39 goliath kernel: [    1.731752] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul  2 17:01:39 goliath kernel: [    1.731802] mice: PS/2 mouse device common for all mice
Jul  2 17:01:39 goliath kernel: [    1.731857] rtc_cmos 00:03: RTC can wake from S4
Jul  2 17:01:39 goliath kernel: [    1.731878] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Jul  2 17:01:39 goliath kernel: [    1.731899] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Jul  2 17:01:39 goliath kernel: [    1.731971] device-mapper: uevent: version 1.0.3
Jul  2 17:01:39 goliath kernel: [    1.732034] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Jul  2 17:01:39 goliath kernel: [    1.732125] device-mapper: multipath: version 1.1.0 loaded
Jul  2 17:01:39 goliath kernel: [    1.732127] device-mapper: multipath round-robin: version 1.0.0 loaded
Jul  2 17:01:39 goliath kernel: [    1.732323] cpuidle: using governor ladder
Jul  2 17:01:39 goliath kernel: [    1.732324] cpuidle: using governor menu
Jul  2 17:01:39 goliath kernel: [    1.732545] TCP cubic registered
Jul  2 17:01:39 goliath kernel: [    1.732633] NET: Registered protocol family 10
Jul  2 17:01:39 goliath kernel: [    1.732928] lo: Disabled Privacy Extensions
Jul  2 17:01:39 goliath kernel: [    1.733095] NET: Registered protocol family 17
Jul  2 17:01:39 goliath kernel: [    1.735358] registered taskstats version 1
Jul  2 17:01:39 goliath kernel: [    1.735834]   Magic number: 3:706:31
Jul  2 17:01:39 goliath kernel: [    1.735895] rtc_cmos 00:03: setting system clock to 2011-07-02 15:01:37 UTC (1309618897)
Jul  2 17:01:39 goliath kernel: [    1.735897] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul  2 17:01:39 goliath kernel: [    1.735898] EDD information not available.
Jul  2 17:01:39 goliath kernel: [    2.049231] ata3: SATA link down (SStatus 0 SControl 300)
Jul  2 17:01:39 goliath kernel: [    2.059913] ata4: SATA link down (SStatus 0 SControl 300)
Jul  2 17:01:39 goliath kernel: [    2.059933] usb 2-3: new high speed USB device using ehci_hcd and address 2
Jul  2 17:01:39 goliath kernel: [    2.210411] usb 2-3: configuration #1 chosen from 1 choice
Jul  2 17:01:39 goliath kernel: [    2.388297] ata2.00: SATA link down (SStatus 0 SControl 300)
Jul  2 17:01:39 goliath kernel: [    2.388308] ata2.01: SATA link down (SStatus 0 SControl 300)
Jul  2 17:01:39 goliath kernel: [    2.398988] ata1.00: SATA link down (SStatus 0 SControl 300)
Jul  2 17:01:39 goliath kernel: [    2.399000] ata1.01: SATA link down (SStatus 0 SControl 300)
Jul  2 17:01:39 goliath kernel: [    2.399029] Freeing unused kernel memory: 888k freed
Jul  2 17:01:39 goliath kernel: [    2.399126] Write protecting the kernel read-only data: 7688k
Jul  2 17:01:39 goliath kernel: [    2.406839] udev: starting version 151
Jul  2 17:01:39 goliath kernel: [    2.426646] pata_marvell 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jul  2 17:01:39 goliath kernel: [    2.427252] scsi4 : pata_marvell
Jul  2 17:01:39 goliath kernel: [    2.427438] scsi5 : pata_marvell
Jul  2 17:01:39 goliath kernel: [    2.427473] ata5: PATA max UDMA/100 cmd 0xcc00 ctl 0xc880 bmdma 0xc400 irq 19
Jul  2 17:01:39 goliath kernel: [    2.427475] ata6: PATA max UDMA/133 cmd 0xc800 ctl 0xc480 bmdma 0xc408 irq 19
Jul  2 17:01:39 goliath kernel: [    2.427795] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jul  2 17:01:39 goliath kernel: [    2.427809] r8169 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jul  2 17:01:39 goliath kernel: [    2.428221] eth0: RTL8168c/8111c at 0xffffc90013dc4000, 90:e6:ba:aa:7d:91, XID 1c4000c0 IRQ 55
Jul  2 17:01:39 goliath kernel: [    2.428786] megasas: 00.00.04.01 Thu July 24 11:41:51 PST 2008
Jul  2 17:01:39 goliath kernel: [    2.428796] megasas: 0x1000:0x0079:0x1000:0x9261: bus 5:slot 0:func 0
Jul  2 17:01:39 goliath kernel: [    2.428811] megaraid_sas 0000:05:00.0: PCI INT A -> GSI 35 (level, low) -> IRQ 35
Jul  2 17:01:39 goliath kernel: [    2.428849] megasas: FW now in Ready state
Jul  2 17:01:39 goliath kernel: [    2.431388] Initializing USB Mass Storage driver...
Jul  2 17:01:39 goliath kernel: [    2.431447] scsi7 : SCSI emulation for USB Mass Storage devices
Jul  2 17:01:39 goliath kernel: [    2.431495] usbcore: registered new interface driver usb-storage
Jul  2 17:01:39 goliath kernel: [    2.431496] USB Mass Storage support registered.
Jul  2 17:01:39 goliath kernel: [    2.431524] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jul  2 17:01:39 goliath kernel: [    2.431536] r8169 0000:08:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jul  2 17:01:39 goliath kernel: [    2.431930] eth1: RTL8168c/8111c at 0xffffc90003076000, 90:e6:ba:aa:7e:b7, XID 1c4000c0 IRQ 56
Jul  2 17:01:39 goliath kernel: [    2.467876] scsi6 : LSI SAS based MegaRAID driver
Jul  2 17:01:39 goliath kernel: [    2.475196] scsi 6:0:16:0: Direct-Access     ATA      WDC WD20EARS-00M AB50 PQ: 0 ANSI: 5
Jul  2 17:01:39 goliath kernel: [    2.484784] scsi 6:0:17:0: Direct-Access     ATA      WDC WD20EARS-00J 0A80 PQ: 0 ANSI: 5
Jul  2 17:01:39 goliath kernel: [    2.491758] scsi 6:0:18:0: Direct-Access     ATA      WDC WD20EARS-00M AB50 PQ: 0 ANSI: 5
Jul  2 17:01:39 goliath kernel: [    2.503215] scsi 6:0:19:0: Direct-Access     ATA      WDC WD20EARS-00J 0A80 PQ: 0 ANSI: 5
Jul  2 17:01:39 goliath kernel: [    2.517049] scsi 6:0:20:0: Direct-Access     ATA      OCZ-VERTEX2      1.24 PQ: 0 ANSI: 5
Jul  2 17:01:39 goliath kernel: [    2.531324] scsi 6:0:21:0: Direct-Access     ATA      OCZ-VERTEX2      1.24 PQ: 0 ANSI: 5
Jul  2 17:01:39 goliath kernel: [    2.552514] scsi 6:0:22:0: Direct-Access     ATA      OCZ-VERTEX2      1.24 PQ: 0 ANSI: 5
Jul  2 17:01:39 goliath kernel: [    2.565803] scsi 6:0:23:0: Direct-Access     ATA      OCZ-VERTEX2      1.24 PQ: 0 ANSI: 5
Jul  2 17:01:39 goliath kernel: [    2.575035] scsi 6:2:0:0: Direct-Access     LSI      MR9260-8i        2.70 PQ: 0 ANSI: 5
Jul  2 17:01:39 goliath kernel: [    2.575126] scsi 6:2:1:0: Direct-Access     LSI      MR9260-8i        2.70 PQ: 0 ANSI: 5
Jul  2 17:01:39 goliath kernel: [    2.581063] sd 6:2:0:0: [sda] 464519168 512-byte logical blocks: (237 GB/221 GiB)
Jul  2 17:01:39 goliath kernel: [    2.581077] sd 6:2:0:0: Attached scsi generic sg0 type 0
Jul  2 17:01:39 goliath kernel: [    2.581127] sd 6:2:0:0: [sda] Write Protect is off
Jul  2 17:01:39 goliath kernel: [    2.581166] sd 6:2:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  2 17:01:39 goliath kernel: [    2.581236] sd 6:2:1:0: [sdb] 11717836800 512-byte logical blocks: (5.99 TB/5.45 TiB)
Jul  2 17:01:39 goliath kernel: [    2.581245] sd 6:2:1:0: Attached scsi generic sg1 type 0
Jul  2 17:01:39 goliath kernel: [    2.581291] sd 6:2:1:0: [sdb] Write Protect is off
Jul  2 17:01:39 goliath kernel: [    2.581328] sd 6:2:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  2 17:01:39 goliath kernel: [    2.581333]  sda: sda1 sda2 <
Jul  2 17:01:39 goliath kernel: [    2.581683]  sdb: sda5 >
Jul  2 17:01:39 goliath kernel: [    2.582087] sd 6:2:0:0: [sda] Attached SCSI disk
Jul  2 17:01:39 goliath kernel: [    2.583950]  unknown partition table
Jul  2 17:01:39 goliath kernel: [    2.584229] sd 6:2:1:0: [sdb] Attached SCSI disk
Jul  2 17:01:39 goliath kernel: [    2.767220] usb 7-2: new full speed USB device using uhci_hcd and address 2
Jul  2 17:01:39 goliath kernel: [    2.787595] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
Jul  2 17:01:39 goliath kernel: [    2.787597] EXT4-fs (sda1): write access will be enabled during recovery
Jul  2 17:01:39 goliath kernel: [    2.821713] EXT4-fs (sda1): orphan cleanup on readonly fs
Jul  2 17:01:39 goliath kernel: [    2.821753] EXT4-fs (sda1): 5 orphan inodes deleted
Jul  2 17:01:39 goliath kernel: [    2.821755] EXT4-fs (sda1): recovery complete
Jul  2 17:01:39 goliath kernel: [    2.822213] EXT4-fs (sda1): mounted filesystem with ordered data mode
Jul  2 17:01:39 goliath kernel: [    2.962053] usb 7-2: configuration #1 chosen from 1 choice
Jul  2 17:01:39 goliath kernel: [    3.248019] usb 8-1: new full speed USB device using uhci_hcd and address 2
Jul  2 17:01:39 goliath kernel: [    3.428757] usb 8-1: configuration #1 chosen from 1 choice
Jul  2 17:01:39 goliath kernel: [    3.507470] Adding 974840k swap on /dev/sda5.  Priority:-1 extents:1 across:974840k 
Jul  2 17:01:39 goliath kernel: [    3.513019] udev: starting version 151
Jul  2 17:01:39 goliath kernel: [    3.519644] lp: driver loaded but no devices found
Jul  2 17:01:39 goliath kernel: [    3.523335] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul  2 17:01:39 goliath kernel: [    3.532433] vga16fb: mapped to 0xffff8800000a0000
Jul  2 17:01:39 goliath kernel: [    3.532476] fb0: VGA16 VGA frame buffer device
Jul  2 17:01:39 goliath kernel: [    3.536800] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Jul  2 17:01:39 goliath kernel: [    3.536803] Disabling lock debugging due to kernel taint
Jul  2 17:01:39 goliath kernel: [    3.560747] type=1505 audit(1309618899.322:2):  operation="profile_load" pid=698 name="/sbin/dhclient3"
Jul  2 17:01:39 goliath kernel: [    3.561139] type=1505 audit(1309618899.322:3):  operation="profile_load" pid=698 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jul  2 17:01:39 goliath kernel: [    3.561366] type=1505 audit(1309618899.322:4):  operation="profile_load" pid=698 name="/usr/lib/connman/scripts/dhclient-script"
Jul  2 17:01:39 goliath kernel: [    3.605685] [fglrx] Maximum main memory to use for locked dma buffers: 23638 MBytes.
Jul  2 17:01:39 goliath kernel: [    3.605769] [fglrx]   vendor: 1002 device: 6738 count: 1
Jul  2 17:01:39 goliath kernel: [    3.606128] [fglrx] ioport: bar 4, base 0xb000, size: 0x100
Jul  2 17:01:39 goliath kernel: [    3.606145] pci 0000:06:00.0: PCI INT A -> GSI 30 (level, low) -> IRQ 30
Jul  2 17:01:39 goliath kernel: [    3.606356] coretemp coretemp.0: Unable to access MSR 0xEE, for Tjmax, left at default
Jul  2 17:01:39 goliath kernel: [    3.606401] coretemp coretemp.1: Unable to access MSR 0xEE, for Tjmax, left at default
Jul  2 17:01:39 goliath kernel: [    3.606461] [fglrx] Kernel PAT support is enabled
Jul  2 17:01:39 goliath kernel: [    3.606476] [fglrx] module loaded - fglrx 8.86.5 [May 24 2011] with 1 minors
Jul  2 17:01:39 goliath kernel: [    3.606478] coretemp coretemp.2: Unable to access MSR 0xEE, for Tjmax, left at default
Jul  2 17:01:39 goliath kernel: [    3.606503] coretemp coretemp.3: Unable to access MSR 0xEE, for Tjmax, left at default
Jul  2 17:01:39 goliath kernel: [    3.620732] usbcore: registered new interface driver hiddev
Jul  2 17:01:39 goliath kernel: [    3.622189] w83627ehf: Found W83667HG chip at 0x290
Jul  2 17:01:39 goliath kernel: [    3.622205] ACPI: resource w83627ehf [0x295-0x296] conflicts with ACPI region HWRE [0x290-0x299]
Jul  2 17:01:39 goliath kernel: [    3.622207] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jul  2 17:01:39 goliath kernel: [    3.623500] input: Logitech Logitech Illuminated Keyboard as /devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.0/input/input3
Jul  2 17:01:39 goliath kernel: [    3.623555] generic-usb 0003:046D:C318.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech Logitech Illuminated Keyboard] on usb-0000:00:1d.1-2/input0
Jul  2 17:01:39 goliath kernel: [    3.627648] input: Logitech Logitech Illuminated Keyboard as /devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.1/input/input4
Jul  2 17:01:39 goliath kernel: [    3.627939] generic-usb 0003:046D:C318.0002: input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech Logitech Illuminated Keyboard] on usb-0000:00:1d.1-2/input1
Jul  2 17:01:39 goliath kernel: [    3.630605] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.0/input/input5
Jul  2 17:01:39 goliath kernel: [    3.630678] generic-usb 0003:046D:C526.0003: input,hidraw2: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.2-1/input0
Jul  2 17:01:39 goliath kernel: [    3.635572] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.1/input/input6
Jul  2 17:01:39 goliath kernel: [    3.635657] generic-usb 0003:046D:C526.0004: input,hiddev97,hidraw3: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.2-1/input1
Jul  2 17:01:39 goliath kernel: [    3.635677] usbcore: registered new interface driver usbhid
Jul  2 17:01:39 goliath kernel: [    3.635679] usbhid: v2.6:USB HID core driver
Jul  2 17:01:39 goliath kernel: [    3.657146] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jul  2 17:01:39 goliath kernel: [    3.765675] EXT4-fs (sdb): mounted filesystem with ordered data mode
Jul  2 17:01:39 goliath kernel: [    3.806021] Console: switching to colour frame buffer device 80x30
Jul  2 17:01:39 goliath kernel: [    3.825542] type=1505 audit(1309618899.582:5):  operation="profile_load" pid=1008 name="/usr/share/gdm/guest-session/Xsession"
Jul  2 17:01:39 goliath kernel: [    3.825662] type=1505 audit(1309618899.582:6):  operation="profile_replace" pid=1009 name="/sbin/dhclient3"
Jul  2 17:01:39 goliath kernel: [    3.825670] type=1505 audit(1309618899.582:7):  operation="profile_load" pid=1014 name="/usr/sbin/tcpdump"
Jul  2 17:01:39 goliath kernel: [    3.825676] type=1505 audit(1309618899.582:8):  operation="profile_load" pid=1013 name="/usr/sbin/mysqld"
Jul  2 17:01:39 goliath kernel: [    3.826072] type=1505 audit(1309618899.582:9):  operation="profile_replace" pid=1009 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jul  2 17:01:39 goliath kernel: [    3.826307] type=1505 audit(1309618899.592:10):  operation="profile_replace" pid=1009 name="/usr/lib/connman/scripts/dhclient-script"
Jul  2 17:01:39 goliath kernel: [    3.832316] r8169: eth0: link down
Jul  2 17:01:39 goliath kernel: [    3.832322] r8169: eth0: link down
Jul  2 17:01:39 goliath kernel: [    3.833757] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul  2 17:01:39 goliath kernel: [    3.858847] r8169: eth1: link down
Jul  2 17:01:39 goliath kernel: [    3.859688] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jul  2 17:01:39 goliath kernel: [    4.119720] hda_codec: AD1989B: BIOS auto-probing.
Jul  2 17:01:39 goliath kernel: [    4.119824] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input7
Jul  2 17:01:39 goliath kernel: [    4.127705] HDA Intel 0000:06:00.1: PCI INT B -> GSI 37 (level, low) -> IRQ 37
Jul  2 17:01:40 goliath kernel: [    4.724197] vboxdrv: fAsync=0 offMin=0x1f5 offMax=0x139e
Jul  2 17:01:40 goliath kernel: [    4.724287] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Jul  2 17:01:41 goliath kernel: [    5.225481] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x002f0d00
Jul  2 17:01:41 goliath kernel: [    5.251538] r8169: eth0: link up
Jul  2 17:01:41 goliath kernel: [    5.252400] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jul  2 17:01:41 goliath kernel: [    5.261139] ppdev: user-space parallel port driver
Jul  2 17:01:41 goliath kernel: [    5.483935] [fglrx] Firegl kernel thread PID: 1480
Jul  2 17:01:41 goliath kernel: [    5.483961] [fglrx] Firegl kernel thread PID: 1481
Jul  2 17:01:41 goliath kernel: [    5.483985] [fglrx] Firegl kernel thread PID: 1482
Jul  2 17:01:41 goliath kernel: [    5.484345] [fglrx] IRQ 57 Enabled
Jul  2 17:01:41 goliath kernel: [    5.890590] [fglrx] Gart USWC size:1280 M.
Jul  2 17:01:41 goliath kernel: [    5.890593] [fglrx] Gart cacheable size:508 M.
Jul  2 17:01:41 goliath kernel: [    5.890596] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Jul  2 17:01:41 goliath kernel: [    5.890597] [fglrx] Reserved FB block: Unshared offset:fbfd000, size:403000 
Jul  2 17:01:41 goliath kernel: [    5.890599] [fglrx] Reserved FB block: Unshared offset:3fff4000, size:c000 
Jul  2 17:01:43 goliath kernel: [    7.425253] scsi 7:0:0:0: Direct-Access     Kingston DataTraveler G2  1.00 PQ: 0 ANSI: 2
Jul  2 17:01:43 goliath kernel: [    7.425530] sd 7:0:0:0: Attached scsi generic sg2 type 0
Jul  2 17:01:43 goliath kernel: [    7.426249] sd 7:0:0:0: [sdc] 15636304 512-byte logical blocks: (8.00 GB/7.45 GiB)
Jul  2 17:01:43 goliath kernel: [    7.426744] sd 7:0:0:0: [sdc] Write Protect is off
Jul  2 17:01:43 goliath kernel: [    7.428872]  sdc: sdc1
Jul  2 17:01:43 goliath kernel: [    7.430620] sd 7:0:0:0: [sdc] Attached SCSI removable disk
Jul  2 17:01:44 goliath kernel: [    8.635838] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
```

---

### Post by 448191 on 2011-07-02
RAID BIOS now suddenly claimed no card present. Placed in different slot and reset BIOS yet again.

The RAID card runs very hot. But maximum ambient temperature is listed as 44.5C (60C with BBU). It's doubtful it ever reached that.

---

### Post by 448191 on 2011-07-02
It's stable so far, but the slot it's in runs at just 4x instead of the 8x the card is capable of..

---

### Post by 448191 on 2011-07-03
I changed slots again, recreated the raid 0 array, reinstalled everything, but on a cold boot, the lsi bios will claim no card is present.

I have had this message before, I figured it was because I changed slots and the raid card loaded part or it's firmware into the bios "option rom", meaning it would look at the wrong PCI address. But now a cold boot will fail, yet following reboots work fine. The "no space for option rom" message is gone btw, that's a matter of disabling the onboard sas controller.

Still a bit confused but it seems more likely the MB is the culprit. Not surprising, I've had some negative experiences with Asus (and Gigabyte) boards in the past. Just give me a basic motherboard without all the fluff for christs sake.

Problem is that when I say "basic", I really mean a socket 1366, ECC capable board with at least one PCIe 16x and one 8x slot. I really haven't seen many of those.

Of course it could still be the RAID controller or the SSDs that are at fault.

---

