---
title: "Ubuntu 8.10 random 'standby'?"
date: 2009-04-02
forum: General Help
---

### Post by europa on 2009-04-02
Hi there.

I've been happily using ubuntu for about a year now.  Recently I'm having a strange issue.

When I am using the computer, the monitor turns off and gives me the 'no signal detected' message.  I'm unable to SSH or VNC to the computer using my other computers.  It is as if the computer goes instantly into standby mode for some reason.

The physical computer sounds as though it is still running.  I have to push the power button until the power turns off in order to get the computer up and running again.

It happens randomly all the time. It could be 1 minute after the computer has started, or it may remain turned on all night.

Is this a known issue? I've looked through the forums but im not sure exactly what i'm looking for.  Is there a log file I can check to see whats going on?

Any help would be appreciated. Thanks

---

### Post by Roidhun on 2009-04-02
I find myself having similar problems on 8.04. One machine freezes constantly at around 20-40 min intervals.
Symptoms are: Blinking lights on keyboard, screen frozen, mouse cursor immovable, no network connection. System appears to be physically running, but with little or no activity. 

The only cure is a hard reset or power off/power on.

Booting may freeze at the "Starting up" message or in the image with the moving bar, in which case a couple of extra resets/power cyclings usually help things along.

Logs show nothing.

I'm clueless, I hope some of you aren't...

---

### Post by kryptikos on 2009-04-02
> **europa said:**
> Hi there.

I've been happily using ubuntu for about a year now.  Recently I'm having a strange issue.

When I am using the computer, the monitor turns off and gives me the 'no signal detected' message.  I'm unable to SSH or VNC to the computer using my other computers.  It is as if the computer goes instantly into standby mode for some reason.

The physical computer sounds as though it is still running.  I have to push the power button until the power turns off in order to get the computer up and running again.

It happens randomly all the time. It could be 1 minute after the computer has started, or it may remain turned on all night.

Is this a known issue? I've looked through the forums but im not sure exactly what i'm looking for.  Is there a log file I can check to see whats going on?

Any help would be appreciated. Thanks

Without seeing logs it's a tough call. Shooting from the hip from your description I would be more suspect of hardware than the OS. Randomness is a key indicator. Perhaps the motherboard/cards are gunked up with dust...classic example is video cards, they get hot and blank out. Sometimes as components age the solder gets old, as heat comes on the motherboard or card the points expand until they fail, and contract again upon cooling. As a starting point I'd crack the case, blow some air through it and clean the gunk out. 

As far as logs to check, look through:

sudo less /var/log/messages
sudo dmesg

You could also check through Xorg.0.log.

---

### Post by europa on 2009-04-02
Thanks for your response, Kryptikos.

I'm not at home at the moment, but I can tell you there is not much dust in my computer.  I had some RAM fail a month or so back and before i switched it out I took a can of compressed air to that sob. heh.

The computer is about 18 months old.  I wouldn't expect components to be failing so soon.

I will check the log files when I get home.

Thanks for the help.

---

### Post by europa on 2009-04-02
Ok. Here is the last minute of /var/log/messages before i restarted.

```
Apr  2 19:55:10 jack-desktop kernel: [   29.159982] VBoxDrv: dbg - g_abExecMemory=ffffffffa0702fe0
Apr  2 19:55:10 jack-desktop kernel: [   29.160012] vboxdrv: fAsync=1 offMin=0x83bed offMax=0x83bed
Apr  2 19:55:10 jack-desktop kernel: [   29.160086] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
Apr  2 19:55:11 jack-desktop kernel: [   29.368067] VBoxNetFlt: dbg - g_abExecMemory=ffffffffa08a0e20
Apr  2 19:55:12 jack-desktop kernel: [   30.370296] Bluetooth: Core ver 2.13
Apr  2 19:55:12 jack-desktop kernel: [   30.371191] NET: Registered protocol family 31
Apr  2 19:55:12 jack-desktop kernel: [   30.371198] Bluetooth: HCI device and connection manager initialized
Apr  2 19:55:12 jack-desktop kernel: [   30.371203] Bluetooth: HCI socket layer initialized
Apr  2 19:55:12 jack-desktop kernel: [   30.382268] Bluetooth: L2CAP ver 2.11
Apr  2 19:55:12 jack-desktop kernel: [   30.382274] Bluetooth: L2CAP socket layer initialized
Apr  2 19:55:12 jack-desktop kernel: [   30.392044] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Apr  2 19:55:12 jack-desktop kernel: [   30.392052] Bluetooth: BNEP filters: protocol multicast
Apr  2 19:55:12 jack-desktop kernel: [   30.417495] Bridge firewalling registered
Apr  2 19:55:12 jack-desktop kernel: [   30.428224] Bluetooth: SCO (Voice Link) ver 0.6
Apr  2 19:55:12 jack-desktop kernel: [   30.428230] Bluetooth: SCO socket layer initialized
Apr  2 19:55:12 jack-desktop kernel: [   30.478265] Bluetooth: RFCOMM socket layer initialized
Apr  2 19:55:12 jack-desktop kernel: [   30.478629] Bluetooth: RFCOMM TTY layer initialized
Apr  2 19:55:12 jack-desktop kernel: [   30.478633] Bluetooth: RFCOMM ver 1.10
Apr  2 19:55:16 jack-desktop kernel: [   34.568617] skge eth1: enabling interface
Apr  2 19:55:16 jack-desktop kernel: [   34.572598] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr  2 19:55:16 jack-desktop kernel: [   34.574579] sky2 eth0: enabling interface
Apr  2 19:55:16 jack-desktop kernel: [   34.577147] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr  2 19:55:16 jack-desktop kernel: [   34.769158] NET: Registered protocol family 17
Apr  2 19:55:17 jack-desktop kernel: [   35.678586] [fglrx] CMM init INV FB MC:0xd0000000, length:0x10000000
Apr  2 19:55:17 jack-desktop kernel: [   35.678600] [fglrx] Reserved FB block: Shared offset:0, size:1000000
Apr  2 19:55:17 jack-desktop kernel: [   35.678603] [fglrx] Reserved FB block: Unshared offset:7ffb000, size:5000
Apr  2 19:55:17 jack-desktop kernel: [   35.678605] [fglrx] Reserved FB block: Unshared offset:ffbc000, size:44000
Apr  2 19:55:18 jack-desktop kernel: [   37.080146] skge eth1: Link is up at 1000 Mbps, full duplex, flow control both
Apr  2 19:55:18 jack-desktop kernel: [   37.080838] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Apr  2 23:43:43 jack-desktop syslogd 1.5.0#2ubuntu6: restart.
Apr  2 23:43:43 jack-desktop kernel: Inspecting /boot/System.map-2.6.27-11-generic
Apr  2 23:43:43 jack-desktop kernel: Cannot find map file.
Apr  2 23:43:43 jack-desktop kernel: Loaded 58755 symbols from 101 modules.

```

Any ideas?

---

### Post by europa on 2009-04-03
a little more log from another crash (continues from last log):

```
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] Linux version 2.6.27-11-generic (buildd@crested) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:28:32 UTC 2009 (Ubuntu 2.6.27-11.27-gen
eric)
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] Command line: root=UUID=a49eb874-46df-43c0-8573-e2ddc25160b0 ro quiet splash 
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] KERNEL supported cpus:
Apr  2 23:43:43 jack-desktop kernel: [    0.000000]   Intel GenuineIntel
Apr  2 23:43:43 jack-desktop kernel: [    0.000000]   AMD AuthenticAMD
Apr  2 23:43:43 jack-desktop kernel: [    0.000000]   Centaur CentaurHauls
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Apr  2 23:43:43 jack-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Apr  2 23:43:43 jack-desktop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Apr  2 23:43:43 jack-desktop kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Apr  2 23:43:43 jack-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffa0000 (usable)
Apr  2 23:43:43 jack-desktop kernel: [    0.000000]  BIOS-e820: 000000007ffa0000 - 000000007ffae000 (ACPI data)
Apr  2 23:43:43 jack-desktop kernel: [    0.000000]  BIOS-e820: 000000007ffae000 - 000000007ffe0000 (ACPI NVS)
Apr  2 23:43:43 jack-desktop kernel: [    0.000000]  BIOS-e820: 000000007ffe0000 - 0000000080000000 (reserved)
Apr  2 23:43:43 jack-desktop kernel: [    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] DMI 2.3 present.
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] last_pfn = 0x7ffa0 max_arch_pfn = 0x3ffffffff
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] init_memory_mapping
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] last_map_addr: 7ffa0000 end: 7ffa0000
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] RAMDISK: 377ab000 - 37fef52f
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] ACPI: RSDP 000FAD00, 0014 (r0 ACPIAM)
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] ACPI: RSDT 7FFA0000, 0034 (r1 A M I  OEMRSDT   3000607 MSFT       97)
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] ACPI: FACP 7FFA0200, 0084 (r2 A M I  OEMFACP   3000607 MSFT       97)
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] ACPI: DSDT 7FFA0430, 5B4C (r1  A0466 A0466001        1 INTL  2002026)
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] ACPI: FACS 7FFAE000, 0040
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] ACPI: APIC 7FFA0390, 005C (r1 A M I  OEMAPIC   3000607 MSFT       97)
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] ACPI: MCFG 7FFA03F0, 003C (r1 A M I  OEMMCFG   3000607 MSFT       97)
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] ACPI: OEMB 7FFAE040, 007B (r1 A M I  AMI_OEM   3000607 MSFT       97)
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] No NUMA configuration found
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] Faking a node at 0000000000000000-000000007ffa0000
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] Bootmem setup node 0 0000000000000000-000000007ffa0000
Apr  2 23:43:43 jack-desktop kernel: [    0.000000]   NODE_DATA [0000000000012000 - 0000000000016fff]
Apr  2 23:43:43 jack-desktop kernel: [    0.000000]   bootmap [0000000000017000 -  0000000000026ff7] pages 10
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] (6 early reservations) ==> bootmem [0000000000 - 007ffa0000]
Apr  2 23:43:43 jack-desktop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Apr  2 23:43:43 jack-desktop kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Apr  2 23:43:43 jack-desktop kernel: [    0.000000]   #2 [0000200000 - 00008b9f5c]    TEXT DATA BSS ==> [0000200000 - 00008b9f5c]
Apr  2 23:43:43 jack-desktop kernel: [    0.000000]   #3 [00377ab000 - 0037fef52f]          RAMDISK ==> [00377ab000 - 0037fef52f]
Apr  2 23:43:43 jack-desktop kernel: [    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Apr  2 23:43:43 jack-desktop kernel: [    0.000000]   #5 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] found SMP MP-table at [ffff8800000ff780] 000ff780
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] Zone PFN ranges:
Apr  2 23:43:43 jack-desktop kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Apr  2 23:43:43 jack-desktop kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Apr  2 23:43:43 jack-desktop kernel: [    0.000000]   Normal   0x00100000 -> 0x00100000
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] Movable zone start PFN for each node
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] early_node_map[2] active PFN ranges
Apr  2 23:43:43 jack-desktop kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Apr  2 23:43:43 jack-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x0007ffa0
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] Detected use of extended apic ids on hypertransport bus
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x908
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] Setting APIC routing to flat
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7f700000)
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] PERCPU: Allocating 64928 bytes of per cpu data
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 514064
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] Policy zone: DMA32
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] Kernel command line: root=UUID=a49eb874-46df-43c0-8573-e2ddc25160b0 ro quiet splash 
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] Initializing CPU#0
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] TSC: Unable to calibrate against PIT
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] TSC: using PMTIMER reference calibration
Apr  2 23:43:43 jack-desktop kernel: [    0.000000] Detected 2405.442 MHz processor.
Apr  2 23:43:43 jack-desktop kernel: [    0.004000] Console: colour VGA+ 80x25
Apr  2 23:43:43 jack-desktop kernel: [    0.004000] console [tty0] enabled
Apr  2 23:43:43 jack-desktop kernel: [    0.004000] Checking aperture...
Apr  2 23:43:43 jack-desktop kernel: [    0.004000] No AGP bridge found
Apr  2 23:43:43 jack-desktop kernel: [    0.004000] Node 0: aperture @ 3c76000000 size 32 MB
Apr  2 23:43:43 jack-desktop kernel: [    0.004000] Memory: 2047900k/2096768k available (3116k kernel code, 48416k reserved, 1575k data, 540k init)
Apr  2 23:43:43 jack-desktop kernel: [    0.004000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Apr  2 23:43:43 jack-desktop kernel: [    0.004015] Calibrating delay loop (skipped), value calculated using timer frequency.. 4810.88 BogoMIPS (lpj=9621768)
Apr  2 23:43:43 jack-desktop kernel: [    0.004053] Security Framework initialized
Apr  2 23:43:43 jack-desktop kernel: [    0.004065] SELinux:  Disabled at boot.
Apr  2 23:43:43 jack-desktop kernel: [    0.004090] AppArmor: AppArmor initialized
Apr  2 23:43:43 jack-desktop kernel: [    0.004298] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
Apr  2 23:43:43 jack-desktop kernel: [    0.006954] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
Apr  2 23:43:43 jack-desktop kernel: [    0.008316] Mount-cache hash table entries: 256
Apr  2 23:43:43 jack-desktop kernel: [    0.008597] Initializing cgroup subsys ns
Apr  2 23:43:43 jack-desktop kernel: [    0.008601] Initializing cgroup subsys cpuacct
Apr  2 23:43:43 jack-desktop kernel: [    0.008604] Initializing cgroup subsys memory
Apr  2 23:43:43 jack-desktop kernel: [    0.008622] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Apr  2 23:43:43 jack-desktop kernel: [    0.008624] CPU: L2 Cache: 1024K (64 bytes/line)
Apr  2 23:43:43 jack-desktop kernel: [    0.008626] CPU 0/0 -> Node 0
Apr  2 23:43:43 jack-desktop kernel: [    0.008645] CPU: Physical Processor ID: 0
Apr  2 23:43:43 jack-desktop kernel: [    0.008646] CPU: Processor Core ID: 0
Apr  2 23:43:43 jack-desktop kernel: [    0.010011] ACPI: Core revision 20080609
Apr  2 23:43:43 jack-desktop kernel: [    0.012775] ACPI: Checking initramfs for custom DSDT
Apr  2 23:43:43 jack-desktop kernel: [    0.314726] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr  2 23:43:43 jack-desktop kernel: [    0.354625] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4800+ stepping 02
Apr  2 23:43:43 jack-desktop kernel: [    0.354629] Using local APIC timer interrupts.
Apr  2 23:43:43 jack-desktop kernel: [    0.356025] Detected 12.528 MHz APIC timer.
Apr  2 23:43:43 jack-desktop kernel: [    0.356659] Booting processor 1/1 ip 6000
Apr  2 23:43:43 jack-desktop kernel: [    0.004000] Initializing CPU#1
Apr  2 23:43:43 jack-desktop kernel: [    0.004000] Calibrating delay using timer specific routine.. 4810.95 BogoMIPS (lpj=9621902)
Apr  2 23:43:43 jack-desktop kernel: [    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Apr  2 23:43:43 jack-desktop kernel: [    0.004000] CPU: L2 Cache: 1024K (64 bytes/line)
Apr  2 23:43:43 jack-desktop kernel: [    0.004000] CPU 1/1 -> Node 0
Apr  2 23:43:43 jack-desktop kernel: [    0.004000] CPU: Physical Processor ID: 0
Apr  2 23:43:43 jack-desktop kernel: [    0.004000] CPU: Processor Core ID: 1
Apr  2 23:43:43 jack-desktop kernel: [    0.444225] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 4800+ stepping 02
Apr  2 23:43:43 jack-desktop kernel: [    0.444239] Brought up 2 CPUs
Apr  2 23:43:43 jack-desktop kernel: [    0.444242] Total of 2 processors activated (9621.83 BogoMIPS).
Apr  2 23:43:43 jack-desktop kernel: [    0.444490] net_namespace: 1552 bytes
Apr  2 23:43:43 jack-desktop kernel: [    0.444490] Booting paravirtualized kernel on bare hardware
Apr  2 23:43:43 jack-desktop kernel: [    0.444490] Time:  3:43:20  Date: 04/03/09
Apr  2 23:43:43 jack-desktop kernel: [    0.444490] NET: Registered protocol family 16
Apr  2 23:43:43 jack-desktop kernel: [    0.444490] TOM: 0000000080000000 aka 2048M
Apr  2 23:43:43 jack-desktop kernel: [    0.444490] ACPI: bus type pci registered
Apr  2 23:43:43 jack-desktop kernel: [    0.444490] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Apr  2 23:43:43 jack-desktop kernel: [    0.444490] PCI: Not using MMCONFIG.
Apr  2 23:43:43 jack-desktop kernel: [    0.444490] PCI: Using configuration type 1 for base access
Apr  2 23:43:43 jack-desktop kernel: [    0.459888] ACPI: Interpreter enabled
Apr  2 23:43:43 jack-desktop kernel: [    0.459891] ACPI: (supports S0 S1 S3 S4 S5)
Apr  2 23:43:43 jack-desktop kernel: [    0.459907] ACPI: Using IOAPIC for interrupt routing
Apr  2 23:43:43 jack-desktop kernel: [    0.460088] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Apr  2 23:43:43 jack-desktop kernel: [    0.468745] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
Apr  2 23:43:43 jack-desktop kernel: [    0.480126] PCI: Using MMCONFIG at e0000000 - efffffff
Apr  2 23:43:43 jack-desktop kernel: [    0.492160] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr  2 23:43:43 jack-desktop kernel: [    0.492160] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
Apr  2 23:43:43 jack-desktop kernel: [    0.492160] pci 0000:00:02.0: PME# disabled
Apr  2 23:43:43 jack-desktop kernel: [    0.492160] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
Apr  2 23:43:43 jack-desktop kernel: [    0.492160] pci 0000:00:05.0: PME# disabled
Apr  2 23:43:43 jack-desktop kernel: [    0.492160] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
Apr  2 23:43:43 jack-desktop kernel: [    0.492160] pci 0000:00:06.0: PME# disabled
Apr  2 23:43:43 jack-desktop kernel: [    0.492502] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Apr  2 23:43:43 jack-desktop kernel: [    0.492506] pci 0000:00:1c.3: PME# disabled
Apr  2 23:43:43 jack-desktop kernel: [    0.492584] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
Apr  2 23:43:43 jack-desktop kernel: [    0.492588] pci 0000:00:1d.0: PME# disabled
Apr  2 23:43:43 jack-desktop kernel: [    0.492705] pci 0000:00:1e.1: quirk: region 0900-093f claimed by ali7101 ACPI
Apr  2 23:43:43 jack-desktop kernel: [    0.492872] pci 0000:00:1f.1: PME# supported from D3hot
Apr  2 23:43:43 jack-desktop kernel: [    0.492875] pci 0000:00:1f.1: PME# disabled
Apr  2 23:43:43 jack-desktop kernel: [    0.493364] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr  2 23:43:43 jack-desktop kernel: [    0.493368] pci 0000:02:00.0: PME# disabled
Apr  2 23:43:43 jack-desktop kernel: [    0.493625] pci 0000:01:13.0: PME# supported from D0 D1 D2 D3hot
Apr  2 23:43:43 jack-desktop kernel: [    0.493629] pci 0000:01:13.0: PME# disabled
Apr  2 23:43:43 jack-desktop kernel: [    0.493730] pci 0000:01:14.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr  2 23:43:43 jack-desktop kernel: [    0.493734] pci 0000:01:14.0: PME# disabled
Apr  2 23:43:43 jack-desktop kernel: [    0.496208] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11 12 14 *15), disabled.
Apr  2 23:43:43 jack-desktop kernel: [    0.496409] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Apr  2 23:43:43 jack-desktop kernel: [    0.496605] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Apr  2 23:43:43 jack-desktop kernel: [    0.496800] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Apr  2 23:43:43 jack-desktop kernel: [    0.500080] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Apr  2 23:43:43 jack-desktop kernel: [    0.500277] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Apr  2 23:43:43 jack-desktop kernel: [    0.500471] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 7 10 11 12 14 15)
Apr  2 23:43:43 jack-desktop kernel: [    0.500669] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15), disabled.
Apr  2 23:43:43 jack-desktop kernel: [    0.500865] ACPI: PCI Interrupt Link [LNKP] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Apr  2 23:43:43 jack-desktop kernel: [    0.500916] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - 43, should be 15 [20080609]
Apr  2 23:43:43 jack-desktop kernel: [    0.500916] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr  2 23:43:43 jack-desktop kernel: [    0.500916] pnp: PnP ACPI init
Apr  2 23:43:43 jack-desktop kernel: [    0.500916] ACPI: bus type pnp registered
Apr  2 23:43:43 jack-desktop kernel: [    0.505646] pnp 00:09: mem resource (0xc0000000-0xc0000fff) overlaps 0000:00:02.0 BAR 9 (0xc0000000-0xcfffffff), disabling
Apr  2 23:43:43 jack-desktop kernel: [    0.505646] pnp 00:09: io resource (0x900-0x91f) overlaps 0000:00:1e.1 BAR 7 (0x900-0x93f), disabling
Apr  2 23:43:43 jack-desktop kernel: [    0.505646] pnp 00:09: mem resource (0xc0000000-0xc0000fff) overlaps 0000:04:00.0 BAR 0 (0xc0000000-0xcfffffff), disabling
Apr  2 23:43:43 jack-desktop kernel: [    0.508955] pnp: PnP ACPI: found 15 devices
Apr  2 23:43:43 jack-desktop kernel: [    0.508955] ACPI: ACPI bus type pnp unregistered
Apr  2 23:43:43 jack-desktop kernel: [    0.508955] PCI: Using ACPI for IRQ routing
Apr  2 23:43:43 jack-desktop kernel: [    0.528040] NET: Registered protocol family 8
Apr  2 23:43:43 jack-desktop kernel: [    0.528042] NET: Registered protocol family 20
Apr  2 23:43:43 jack-desktop kernel: [    0.528063] NetLabel: Initializing
Apr  2 23:43:43 jack-desktop kernel: [    0.528064] NetLabel:  domain hash size = 128
Apr  2 23:43:43 jack-desktop kernel: [    0.528065] NetLabel:  protocols = UNLABELED CIPSOv4
Apr  2 23:43:43 jack-desktop kernel: [    0.528083] NetLabel:  unlabeled traffic allowed by default
Apr  2 23:43:43 jack-desktop kernel: [    0.529311] tracer: 1286 pages allocated for 65536 entries of 80 bytes
Apr  2 23:43:43 jack-desktop kernel: [    0.529312]    actual entries 65586
Apr  2 23:43:43 jack-desktop kernel: [    0.529589] AppArmor: AppArmor Filesystem Enabled
Apr  2 23:43:43 jack-desktop kernel: [    0.529612] ACPI: RTC can wake from S4
Apr  2 23:43:43 jack-desktop kernel: [    0.544061] system 00:09: ioport range 0x28d-0x28e has been reserved
Apr  2 23:43:43 jack-desktop kernel: [    0.544064] system 00:09: ioport range 0x480-0x48f has been reserved
Apr  2 23:43:43 jack-desktop kernel: [    0.544066] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
Apr  2 23:43:43 jack-desktop kernel: [    0.544068] system 00:09: ioport range 0x900-0x9bf could not be reserved
Apr  2 23:43:43 jack-desktop kernel: [    0.544071] system 00:09: ioport range 0x9c0-0x9df has been reserved
Apr  2 23:43:43 jack-desktop kernel: [    0.544074] system 00:09: iomem range 0xff000000-0xffffffff could not be reserved
Apr  2 23:43:43 jack-desktop kernel: [    0.544080] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
Apr  2 23:43:43 jack-desktop kernel: [    0.544082] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
Apr  2 23:43:43 jack-desktop kernel: [    0.544087] system 00:0c: ioport range 0xc00-0xc0f has been reserved
Apr  2 23:43:43 jack-desktop kernel: [    0.544089] system 00:0c: ioport range 0xd00-0xd0f has been reserved
Apr  2 23:43:43 jack-desktop kernel: [    0.544091] system 00:0c: ioport range 0xa20-0xa2f has been reserved
Apr  2 23:43:43 jack-desktop kernel: [    0.544093] system 00:0c: ioport range 0xa30-0xa3f has been reserved
Apr  2 23:43:43 jack-desktop kernel: [    0.544098] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
Apr  2 23:43:43 jack-desktop kernel: [    0.544103] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
Apr  2 23:43:43 jack-desktop kernel: [    0.544105] system 00:0e: iomem range 0xc0000-0xcffff has been reserved
Apr  2 23:43:43 jack-desktop kernel: [    0.544107] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
Apr  2 23:43:43 jack-desktop kernel: [    0.544110] system 00:0e: iomem range 0x100000-0x7fffffff could not be reserved
Apr  2 23:43:43 jack-desktop kernel: [    0.544113] system 00:0e: iomem range 0xfff80000-0xffffffff could not be reserved
Apr  2 23:43:43 jack-desktop kernel: [    0.549559] pci 0000:00:02.0: PCI bridge, secondary bus 0000:04
Apr  2 23:43:43 jack-desktop kernel: [    0.549562] pci 0000:00:02.0:   IO window: 0xe000-0xefff
Apr  2 23:43:43 jack-desktop kernel: [    0.549566] pci 0000:00:02.0:   MEM window: 0xdff00000-0xdfffffff
Apr  2 23:43:43 jack-desktop kernel: [    0.549569] pci 0000:00:02.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
Apr  2 23:43:43 jack-desktop kernel: [    0.549573] pci 0000:00:05.0: PCI bridge, secondary bus 0000:03
Apr  2 23:43:43 jack-desktop kernel: [    0.549576] pci 0000:00:05.0:   IO window: 0xd000-0xdfff
Apr  2 23:43:43 jack-desktop kernel: [    0.549579] pci 0000:00:05.0:   MEM window: 0xdfe00000-0xdfefffff
Apr  2 23:43:43 jack-desktop kernel: [    0.549581] pci 0000:00:05.0:   PREFETCH window: disabled
Apr  2 23:43:43 jack-desktop kernel: [    0.549585] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02
Apr  2 23:43:43 jack-desktop kernel: [    0.549587] pci 0000:00:06.0:   IO window: 0xc000-0xcfff
Apr  2 23:43:43 jack-desktop kernel: [    0.549590] pci 0000:00:06.0:   MEM window: 0xdfd00000-0xdfdfffff
Apr  2 23:43:43 jack-desktop kernel: [    0.549593] pci 0000:00:06.0:   PREFETCH window: disabled
Apr  2 23:43:43 jack-desktop kernel: [    0.549597] pci 0000:00:1a.0: PCI bridge, secondary bus 0000:01
Apr  2 23:43:43 jack-desktop kernel: [    0.549600] pci 0000:00:1a.0:   IO window: 0xb000-0xbfff
Apr  2 23:43:43 jack-desktop kernel: [    0.549604] pci 0000:00:1a.0:   MEM window: 0xdfc00000-0xdfcfffff
Apr  2 23:43:43 jack-desktop kernel: [    0.549608] pci 0000:00:1a.0:   PREFETCH window: disabled
Apr  2 23:43:43 jack-desktop kernel: [    0.549643] bus: 00 index 0 io port: [0, ffff]
Apr  2 23:43:43 jack-desktop kernel: [    0.549645] bus: 00 index 1 mmio: [0, ffffffffffffffff]
Apr  2 23:43:43 jack-desktop kernel: [    0.549647] bus: 04 index 0 io port: [e000, efff]
Apr  2 23:43:43 jack-desktop kernel: [    0.549648] bus: 04 index 1 mmio: [dff00000, dfffffff]
Apr  2 23:43:43 jack-desktop kernel: [    0.549650] bus: 04 index 2 mmio: [c0000000, cfffffff]
Apr  2 23:43:43 jack-desktop kernel: [    0.549652] bus: 04 index 3 mmio: [0, 0]
Apr  2 23:43:43 jack-desktop kernel: [    0.549653] bus: 03 index 0 io port: [d000, dfff]
Apr  2 23:43:43 jack-desktop kernel: [    0.549655] bus: 03 index 1 mmio: [dfe00000, dfefffff]
Apr  2 23:43:43 jack-desktop kernel: [    0.549657] bus: 03 index 2 mmio: [0, 0]
Apr  2 23:43:43 jack-desktop kernel: [    0.549658] bus: 03 index 3 mmio: [0, 0]
Apr  2 23:43:43 jack-desktop kernel: [    0.549660] bus: 02 index 0 io port: [c000, cfff]
Apr  2 23:43:43 jack-desktop kernel: [    0.549662] bus: 02 index 1 mmio: [dfd00000, dfdfffff]
Apr  2 23:43:43 jack-desktop kernel: [    0.549663] bus: 02 index 2 mmio: [0, 0]
Apr  2 23:43:43 jack-desktop kernel: [    0.549665] bus: 02 index 3 mmio: [0, 0]
Apr  2 23:43:43 jack-desktop kernel: [    0.549666] bus: 01 index 0 io port: [b000, bfff]
Apr  2 23:43:43 jack-desktop kernel: [    0.549668] bus: 01 index 1 mmio: [dfc00000, dfcfffff]
Apr  2 23:43:43 jack-desktop kernel: [    0.549670] bus: 01 index 2 mmio: [0, 0]
Apr  2 23:43:43 jack-desktop kernel: [    0.549671] bus: 01 index 3 mmio: [0, 0]
Apr  2 23:43:43 jack-desktop kernel: [    0.549685] NET: Registered protocol family 2
Apr  2 23:43:43 jack-desktop kernel: [    0.588127] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
Apr  2 23:43:43 jack-desktop kernel: [    0.589286] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
Apr  2 23:43:43 jack-desktop kernel: [    0.594565] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Apr  2 23:43:43 jack-desktop kernel: [    0.595867] TCP: Hash tables configured (established 262144 bind 65536)
Apr  2 23:43:43 jack-desktop kernel: [    0.595871] TCP reno registered
Apr  2 23:43:43 jack-desktop kernel: [    0.604166] NET: Registered protocol family 1
Apr  2 23:43:43 jack-desktop kernel: [    0.604301] checking if image is initramfs... it is
Apr  2 23:43:43 jack-desktop kernel: [    1.226514] Freeing initrd memory: 8465k freed
Apr  2 23:43:43 jack-desktop kernel: [    1.238222] audit: initializing netlink socket (disabled)
Apr  2 23:43:43 jack-desktop kernel: [    1.238247] type=2000 audit(1238730200.236:1): initialized
Apr  2 23:43:43 jack-desktop kernel: [    1.243262] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Apr  2 23:43:43 jack-desktop kernel: [    1.246344] VFS: Disk quotas dquot_6.5.1
Apr  2 23:43:43 jack-desktop kernel: [    1.246438] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Apr  2 23:43:43 jack-desktop kernel: [    1.246559] msgmni has been set to 4016
Apr  2 23:43:43 jack-desktop kernel: [    1.246688] io scheduler noop registered
Apr  2 23:43:43 jack-desktop kernel: [    1.246690] io scheduler anticipatory registered
Apr  2 23:43:43 jack-desktop kernel: [    1.246692] io scheduler deadline registered
Apr  2 23:43:43 jack-desktop kernel: [    1.246839] io scheduler cfq registered (default)
Apr  2 23:43:43 jack-desktop kernel: [    1.246866] pci 0000:00:1a.0: Disabling HT MSI mapping<7>pci 0000:04:00.0: Boot video device
Apr  2 23:43:43 jack-desktop kernel: [    1.705335] pcieport-driver 0000:00:02.0: found MSI capability
Apr  2 23:43:43 jack-desktop kernel: [    1.705579] pcieport-driver 0000:00:05.0: found MSI capability
Apr  2 23:43:43 jack-desktop kernel: [    1.705813] pcieport-driver 0000:00:06.0: found MSI capability
Apr  2 23:43:43 jack-desktop kernel: [    1.757972] Linux agpgart interface v0.103
Apr  2 23:43:43 jack-desktop kernel: [    1.757979] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Apr  2 23:43:43 jack-desktop kernel: [    1.758182] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr  2 23:43:43 jack-desktop kernel: [    1.758939] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr  2 23:43:43 jack-desktop kernel: [    1.761206] brd: module loaded
Apr  2 23:43:43 jack-desktop kernel: [    1.761295] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Apr  2 23:43:43 jack-desktop kernel: [    1.761527] PNP: No PS/2 controller found. Probing ports directly.
Apr  2 23:43:43 jack-desktop kernel: [    1.763562] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr  2 23:43:43 jack-desktop kernel: [    1.763568] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr  2 23:43:43 jack-desktop kernel: [    1.785153] mice: PS/2 mouse device common for all mice
Apr  2 23:43:43 jack-desktop kernel: [    1.785305] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
Apr  2 23:43:43 jack-desktop kernel: [    1.785339] rtc0: alarms up to one month
Apr  2 23:43:43 jack-desktop kernel: [    1.785394] cpuidle: using governor ladder
Apr  2 23:43:43 jack-desktop kernel: [    1.785396] cpuidle: using governor menu
Apr  2 23:43:43 jack-desktop kernel: [    1.785760] TCP cubic registered
Apr  2 23:43:43 jack-desktop kernel: [    1.786001] registered taskstats version 1
Apr  2 23:43:43 jack-desktop kernel: [    1.786161]   Magic number: 5:211:714
Apr  2 23:43:43 jack-desktop kernel: [    1.786337] rtc_cmos 00:02: setting system clock to 2009-04-03 03:43:21 UTC (1238730201)
Apr  2 23:43:43 jack-desktop kernel: [    1.786340] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr  2 23:43:43 jack-desktop kernel: [    1.786342] EDD information not available.
Apr  2 23:43:43 jack-desktop kernel: [    1.786383] Freeing unused kernel memory: 540k freed
Apr  2 23:43:43 jack-desktop kernel: [    1.786939] Write protecting the kernel read-only data: 4352k
Apr  2 23:43:43 jack-desktop kernel: [    1.925193] fuse init (API version 7.9)
Apr  2 23:43:43 jack-desktop kernel: [    2.016296] processor ACPI0007:00: registered as cooling_device0
Apr  2 23:43:43 jack-desktop kernel: [    2.016301] ACPI: Processor [CPU1] (supports 8 throttling states)
Apr  2 23:43:43 jack-desktop kernel: [    2.016362] processor ACPI0007:01: registered as cooling_device1
Apr  2 23:43:43 jack-desktop kernel: [    2.284360] No dock devices found.
Apr  2 23:43:43 jack-desktop kernel: [    2.295811] SCSI subsystem initialized
Apr  2 23:43:43 jack-desktop kernel: [    2.312054] sata_sil24 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr  2 23:43:43 jack-desktop kernel: [    2.326904] scsi0 : sata_sil24
Apr  2 23:43:43 jack-desktop kernel: [    2.327103] scsi1 : sata_sil24
Apr  2 23:43:43 jack-desktop kernel: [    2.327142] ata1: SATA max UDMA/100 host m128@0xdfeffc00 port 0xdfef8000 irq 17
Apr  2 23:43:43 jack-desktop kernel: [    2.327145] ata2: SATA max UDMA/100 host m128@0xdfeffc00 port 0xdfefa000 irq 17
Apr  2 23:43:43 jack-desktop kernel: [    2.362509] usbcore: registered new interface driver usbfs
Apr  2 23:43:43 jack-desktop kernel: [    2.362541] usbcore: registered new interface driver hub
Apr  2 23:43:43 jack-desktop kernel: [    2.369562] usbcore: registered new device driver usb
Apr  2 23:43:43 jack-desktop kernel: [    2.389636] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
Apr  2 23:43:43 jack-desktop kernel: [    4.404040] ata1: SATA link down (SStatus 0 SControl 0)
Apr  2 23:43:43 jack-desktop kernel: [    6.484037] ata2: SATA link down (SStatus 0 SControl 0)
Apr  2 23:43:43 jack-desktop kernel: [    6.484746] ohci_hcd 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr  2 23:43:43 jack-desktop kernel: [    6.484762] ohci_hcd 0000:00:1c.0: OHCI Host Controller
Apr  2 23:43:43 jack-desktop kernel: [    6.484820] ohci_hcd 0000:00:1c.0: new USB bus registered, assigned bus number 1
Apr  2 23:43:43 jack-desktop kernel: [    6.484839] ohci_hcd 0000:00:1c.0: irq 17, io mem 0xdfbfc000
Apr  2 23:43:43 jack-desktop kernel: [    6.543212] usb usb1: configuration #1 chosen from 1 choice
Apr  2 23:43:43 jack-desktop kernel: [    6.543242] hub 1-0:1.0: USB hub found
Apr  2 23:43:43 jack-desktop kernel: [    6.543256] hub 1-0:1.0: 3 ports detected
Apr  2 23:43:43 jack-desktop kernel: [    6.749528] ohci_hcd 0000:00:1c.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
Apr  2 23:43:43 jack-desktop kernel: [    6.749545] ohci_hcd 0000:00:1c.1: OHCI Host Controller
Apr  2 23:43:43 jack-desktop kernel: [    6.749573] ohci_hcd 0000:00:1c.1: new USB bus registered, assigned bus number 2
Apr  2 23:43:43 jack-desktop kernel: [    6.749609] ohci_hcd 0000:00:1c.1: irq 18, io mem 0xdfbfd000
Apr  2 23:43:43 jack-desktop kernel: [    6.806481] usb usb2: configuration #1 chosen from 1 choice
Apr  2 23:43:43 jack-desktop kernel: [    6.806891] hub 2-0:1.0: USB hub found
Apr  2 23:43:43 jack-desktop kernel: [    6.806902] hub 2-0:1.0: 3 ports detected
Apr  2 23:43:43 jack-desktop kernel: [    6.924019] usb 1-2: new low speed USB device using ohci_hcd and address 2
Apr  2 23:43:43 jack-desktop kernel: [    7.012919] ohci_hcd 0000:00:1c.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
Apr  2 23:43:43 jack-desktop kernel: [    7.012930] ohci_hcd 0000:00:1c.2: OHCI Host Controller
Apr  2 23:43:43 jack-desktop kernel: [    7.012956] ohci_hcd 0000:00:1c.2: new USB bus registered, assigned bus number 3
Apr  2 23:43:43 jack-desktop kernel: [    7.012987] ohci_hcd 0000:00:1c.2: irq 19, io mem 0xdfbfe000
Apr  2 23:43:43 jack-desktop kernel: [    7.070470] usb usb3: configuration #1 chosen from 1 choice
Apr  2 23:43:43 jack-desktop kernel: [    7.070873] hub 3-0:1.0: USB hub found
Apr  2 23:43:43 jack-desktop kernel: [    7.070884] hub 3-0:1.0: 3 ports detected
Apr  2 23:43:43 jack-desktop kernel: [    7.153504] usb 1-2: configuration #1 chosen from 1 choice
Apr  2 23:43:43 jack-desktop kernel: [    7.174766] ehci_hcd 0000:00:1c.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Apr  2 23:43:43 jack-desktop kernel: [    7.174776] ehci_hcd 0000:00:1c.3: EHCI Host Controller
Apr  2 23:43:43 jack-desktop kernel: [    7.174807] ehci_hcd 0000:00:1c.3: new USB bus registered, assigned bus number 4
Apr  2 23:43:43 jack-desktop kernel: [    7.196027] ehci_hcd 0000:00:1c.3: debug port 1
Apr  2 23:43:43 jack-desktop kernel: [    7.196052] ehci_hcd 0000:00:1c.3: irq 23, io mem 0xdfbff800
Apr  2 23:43:43 jack-desktop kernel: [    7.333022] usb 2-2: new low speed USB device using ohci_hcd and address 2
Apr  2 23:43:43 jack-desktop kernel: [    7.345038] ehci_hcd 0000:00:1c.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Apr  2 23:43:43 jack-desktop kernel: [    7.345535] usb usb4: configuration #1 chosen from 1 choice
Apr  2 23:43:43 jack-desktop kernel: [    7.345561] hub 4-0:1.0: USB hub found
Apr  2 23:43:43 jack-desktop kernel: [    7.345569] hub 4-0:1.0: 8 ports detected
Apr  2 23:43:43 jack-desktop kernel: [    7.528028] usb 1-2: USB disconnect, address 2
Apr  2 23:43:43 jack-desktop kernel: [    7.553200] sky2 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Apr  2 23:43:43 jack-desktop kernel: [    7.553231] sky2 0000:02:00.0: v1.22 addr 0xdfdfc000 irq 18 Yukon-2 EC rev 2
Apr  2 23:43:43 jack-desktop kernel: [    7.553595] sky2 eth0: addr 00:17:31:1c:36:b3
Apr  2 23:43:43 jack-desktop kernel: [    7.554054] pata_ali 0000:00:1f.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Apr  2 23:43:43 jack-desktop kernel: [    7.556902] scsi2 : pata_ali
Apr  2 23:43:43 jack-desktop kernel: [    7.557825] scsi3 : pata_ali
Apr  2 23:43:43 jack-desktop kernel: [    7.561287] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
Apr  2 23:43:43 jack-desktop kernel: [    7.561289] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
Apr  2 23:43:43 jack-desktop kernel: [    7.880419] ata4.00: ATAPI: LITE-ON DVDRW SOHW-1613S, AS04, max UDMA/66
Apr  2 23:43:43 jack-desktop kernel: [    7.880429] ata4.00: WARNING: ATAPI DMA disabled for reliablity issues.  It can be enabled
Apr  2 23:43:43 jack-desktop kernel: [    7.880431] ata4.00: WARNING: via pata_ali.atapi_dma modparam or corresponding sysfs node.
Apr  2 23:43:43 jack-desktop kernel: [    7.896361] ata4.00: configured for UDMA/66
Apr  2 23:43:43 jack-desktop kernel: [    7.896407] isa bounce pool size: 16 pages
Apr  2 23:43:43 jack-desktop kernel: [    7.897367] scsi 3:0:0:0: CD-ROM            LITE-ON  DVDRW SOHW-1613S AS04 PQ: 0 ANSI: 5
Apr  2 23:43:43 jack-desktop kernel: [    7.897575] scsi 3:0:0:0: Attached scsi generic sg0 type 5
Apr  2 23:43:43 jack-desktop kernel: [    7.897666] skge 0000:01:14.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Apr  2 23:43:43 jack-desktop kernel: [    7.897691] ahci 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Apr  2 23:43:43 jack-desktop kernel: [    7.897735] skge 1.13 addr 0xdfcfc000 irq 21 chip Yukon-Lite rev 9
Apr  2 23:43:43 jack-desktop kernel: [    7.897900] ahci 0000:00:1f.1: AHCI 0001.0000 32 slots 4 ports 3 Gbps 0xf impl IDE mode
Apr  2 23:43:43 jack-desktop kernel: [    7.897903] ahci 0000:00:1f.1: flags: ncq sntf ilck pm led clo pmp pio slum part 
Apr  2 23:43:43 jack-desktop kernel: [    7.898251] skge eth1: addr 00:17:31:1c:32:67
Apr  2 23:43:43 jack-desktop kernel: [    7.898477] ohci1394 0000:01:13.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Apr  2 23:43:43 jack-desktop kernel: [    7.916028] scsi4 : ahci
Apr  2 23:43:43 jack-desktop kernel: [    7.916111] scsi5 : ahci
Apr  2 23:43:43 jack-desktop kernel: [    7.916163] scsi6 : ahci
Apr  2 23:43:43 jack-desktop kernel: [    7.916230] scsi7 : ahci
Apr  2 23:43:43 jack-desktop kernel: [    7.916326] ata5: SATA max UDMA/133 abar m1024@0xdfbffc00 port 0xdfbffd00 irq 2299
Apr  2 23:43:43 jack-desktop kernel: [    7.916330] ata6: SATA max UDMA/133 abar m1024@0xdfbffc00 port 0xdfbffd80 irq 2299
Apr  2 23:43:43 jack-desktop kernel: [    7.916333] ata7: SATA max UDMA/133 abar m1024@0xdfbffc00 port 0xdfbffe00 irq 2299
Apr  2 23:43:43 jack-desktop kernel: [    7.916336] ata8: SATA max UDMA/133 abar m1024@0xdfbffc00 port 0xdfbffe80 irq 2299
Apr  2 23:43:43 jack-desktop kernel: [    7.948296] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[dfcfb800-dfcfbfff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Apr  2 23:43:43 jack-desktop kernel: [    8.060022] usb 1-2: new low speed USB device using ohci_hcd and address 3
Apr  2 23:43:43 jack-desktop kernel: [    8.289797] usb 1-2: configuration #1 chosen from 1 choice
Apr  2 23:43:43 jack-desktop kernel: [    8.294397] usbcore: registered new interface driver hiddev
Apr  2 23:43:43 jack-desktop kernel: [    8.412029] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  2 23:43:43 jack-desktop kernel: [    8.412584] ata5.00: ATA-7: WDC WD2500KS-00MJB0, 02.01C03, max UDMA/133
Apr  2 23:43:43 jack-desktop kernel: [    8.412587] ata5.00: 488397168 sectors, multi 16: LBA48 
Apr  2 23:43:43 jack-desktop kernel: [    8.413165] ata5.00: configured for UDMA/133
Apr  2 23:43:43 jack-desktop kernel: [    8.596020] usb 2-2: new low speed USB device using ohci_hcd and address 3
Apr  2 23:43:43 jack-desktop kernel: [    8.748031] ata6: SATA link down (SStatus 0 SControl 300)
Apr  2 23:43:43 jack-desktop kernel: [    8.810819] usb 2-2: configuration #1 chosen from 1 choice
Apr  2 23:43:43 jack-desktop kernel: [    8.824517] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:1c.0/usb1/1-2/1-2:1.0/input/input1
Apr  2 23:43:43 jack-desktop kernel: [    8.845178] input,hidraw0: USB HID v1.11 Keyboard [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:1c.0-2
Apr  2 23:43:43 jack-desktop kernel: [    8.861319] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:1c.0/usb1/1-2/1-2:1.1/input/input2
Apr  2 23:43:43 jack-desktop kernel: [    8.877080] input,hidraw1: USB HID v1.11 Device [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:1c.0-2
Apr  2 23:43:43 jack-desktop kernel: [    8.884426] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1c.1/usb2/2-2/2-2:1.0/input/input3
Apr  2 23:43:43 jack-desktop kernel: [    8.905085] input,hidraw2: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1c.1-2
Apr  2 23:43:43 jack-desktop kernel: [    8.905105] usbcore: registered new interface driver usbhid
Apr  2 23:43:43 jack-desktop kernel: [    8.905108] usbhid: v2.6:USB HID core driver
Apr  2 23:43:43 jack-desktop kernel: [    9.084033] ata7: SATA link down (SStatus 0 SControl 300)
Apr  2 23:43:43 jack-desktop kernel: [    9.420027] ata8: SATA link down (SStatus 0 SControl 300)
Apr  2 23:43:43 jack-desktop kernel: [    9.436136] scsi 4:0:0:0: Direct-Access     ATA      WDC WD2500KS-00M 02.0 PQ: 0 ANSI: 5
Apr  2 23:43:43 jack-desktop kernel: [    9.436368] scsi 4:0:0:0: Attached scsi generic sg1 type 0
Apr  2 23:43:43 jack-desktop kernel: [    9.464922] Driver 'sr' needs updating - please use bus_type methods
Apr  2 23:43:43 jack-desktop kernel: [    9.468739] Driver 'sd' needs updating - please use bus_type methods
Apr  2 23:43:43 jack-desktop kernel: [    9.471663] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
Apr  2 23:43:43 jack-desktop kernel: [    9.471666] Uniform CD-ROM driver Revision: 3.20
Apr  2 23:43:43 jack-desktop kernel: [    9.471879] sd 4:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Apr  2 23:43:43 jack-desktop kernel: [    9.471893] sd 4:0:0:0: [sda] Write Protect is off
Apr  2 23:43:43 jack-desktop kernel: [    9.471919] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  2 23:43:43 jack-desktop kernel: [    9.471974] sd 4:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Apr  2 23:43:43 jack-desktop kernel: [    9.471985] sd 4:0:0:0: [sda] Write Protect is off
Apr  2 23:43:43 jack-desktop kernel: [    9.472099] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  2 23:43:43 jack-desktop kernel: [    9.472102]  sda: sda1 sda2 < sda5 >
Apr  2 23:43:43 jack-desktop kernel: [    9.504067] sd 4:0:0:0: [sda] Attached SCSI disk
Apr  2 23:43:43 jack-desktop kernel: [    9.761049] PM: Starting manual resume from disk
Apr  2 23:43:43 jack-desktop kernel: [    9.780350] EXT3-fs: INFO: recovery required on readonly filesystem.
Apr  2 23:43:43 jack-desktop kernel: [    9.780355] EXT3-fs: write access will be enabled during recovery.
Apr  2 23:43:43 jack-desktop kernel: [   10.828019] kjournald starting.  Commit interval 5 seconds
Apr  2 23:43:43 jack-desktop kernel: [   10.828039] EXT3-fs: sda1: orphan cleanup on readonly fs
Apr  2 23:43:43 jack-desktop kernel: [   10.828113] EXT3-fs: sda1: 2 orphan inodes deleted
Apr  2 23:43:43 jack-desktop kernel: [   10.828115] EXT3-fs: recovery complete.
Apr  2 23:43:43 jack-desktop kernel: [   10.837468] EXT3-fs: mounted filesystem with ordered data mode.
Apr  2 23:43:43 jack-desktop kernel: [   16.439127] udevd version 124 started
Apr  2 23:43:43 jack-desktop kernel: [   16.861534] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr  2 23:43:43 jack-desktop kernel: [   16.892392] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr  2 23:43:43 jack-desktop kernel: [   17.021532] isp1760 0000:00:1e.1: enabling device (0000 -> 0001)
Apr  2 23:43:43 jack-desktop kernel: [   17.041519] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
Apr  2 23:43:43 jack-desktop kernel: [   17.060034] ACPI: Power Button (FF) [PWRF]
Apr  2 23:43:43 jack-desktop kernel: [   17.060185] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
Apr  2 23:43:43 jack-desktop kernel: [   17.092230] ACPI: Power Button (CM) [PWRB]
Apr  2 23:43:43 jack-desktop kernel: [   17.187321] input: PC Speaker as /devices/platform/pcspkr/input/input6
Apr  2 23:43:43 jack-desktop kernel: [   17.404917] parport_pc 00:06: reported by Plug and Play ACPI
Apr  2 23:43:43 jack-desktop kernel: [   17.405014] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Apr  2 23:43:43 jack-desktop kernel: [   17.517979] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Apr  2 23:43:43 jack-desktop kernel: [   17.580493] [fglrx] Maximum main memory to use for locked dma buffers: 1881 MBytes.
Apr  2 23:43:43 jack-desktop kernel: [   17.580638] [fglrx]   vendor: 1002 device: 7240 count: 1
Apr  2 23:43:43 jack-desktop kernel: [   17.581142] [fglrx] ioport: bar 4, base 0xe800, size: 0x100
Apr  2 23:43:43 jack-desktop kernel: [   17.581867] pci 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Apr  2 23:43:43 jack-desktop kernel: [   17.582911] [fglrx] PAT is enabled successfully!
Apr  2 23:43:43 jack-desktop kernel: [   17.582958] [fglrx] module loaded - fglrx 8.54.3 [Oct 10 2008] with 1 minors
Apr  2 23:43:43 jack-desktop kernel: [   17.643441] ali1535_smbus 0000:00:1e.1: ALI1535_smb region uninitialized - upgrade BIOS?
Apr  2 23:43:43 jack-desktop kernel: [   17.643446] ali1535_smbus 0000:00:1e.1: ALI1535 not detected, module not inserted.
Apr  2 23:43:43 jack-desktop kernel: [   17.705180] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
Apr  2 23:43:43 jack-desktop kernel: [   17.716271] wlan: 0.9.4
Apr  2 23:43:43 jack-desktop kernel: [   17.721539] ath_pci: 0.9.4
Apr  2 23:43:43 jack-desktop kernel: [   17.725991] ath_pci 0000:01:11.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Apr  2 23:43:43 jack-desktop kernel: [   18.320086] ath_rate_sample: 1.2 (0.9.4)
Apr  2 23:43:43 jack-desktop kernel: [   18.320892] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
Apr  2 23:43:43 jack-desktop kernel: [   18.320898] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Apr  2 23:43:43 jack-desktop kernel: [   18.320906] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
Apr  2 23:43:43 jack-desktop kernel: [   18.320909] wifi0: mac 7.8 phy 4.5 radio 5.6
Apr  2 23:43:43 jack-desktop kernel: [   18.320913] wifi0: Use hw queue 1 for WME_AC_BE traffic
Apr  2 23:43:43 jack-desktop kernel: [   18.320915] wifi0: Use hw queue 0 for WME_AC_BK traffic
Apr  2 23:43:43 jack-desktop kernel: [   18.320917] wifi0: Use hw queue 2 for WME_AC_VI traffic
Apr  2 23:43:43 jack-desktop kernel: [   18.320919] wifi0: Use hw queue 3 for WME_AC_VO traffic
Apr  2 23:43:43 jack-desktop kernel: [   18.320920] wifi0: Use hw queue 8 for CAB traffic
Apr  2 23:43:43 jack-desktop kernel: [   18.320922] wifi0: Use hw queue 9 for beacons
Apr  2 23:43:43 jack-desktop kernel: [   18.351277] wifi0: Atheros 5212: mem=0xdfce0000, irq=18
Apr  2 23:43:43 jack-desktop kernel: [   18.724984] HDA Intel 0000:00:1d.0: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Apr  2 23:43:43 jack-desktop kernel: [   20.364138] lp0: using parport0 (interrupt-driven).
Apr  2 23:43:43 jack-desktop kernel: [   20.540826] Adding 6024332k swap on /dev/sda5.  Priority:-1 extents:1 across:6024332k
Apr  2 23:43:43 jack-desktop kernel: [   21.099454] EXT3 FS on sda1, internal journal
Apr  2 23:43:43 jack-desktop kernel: [   22.002195] type=1505 audit(1238730221.749:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4278
Apr  2 23:43:43 jack-desktop kernel: [   22.162405] type=1505 audit(1238730221.909:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4283
Apr  2 23:43:43 jack-desktop kernel: [   22.162709] type=1505 audit(1238730221.909:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4283
Apr  2 23:43:43 jack-desktop kernel: [   22.278030] ip_tables: (C) 2000-2006 Netfilter Core Team
Apr  2 23:43:43 jack-desktop kernel: [   22.863782] ACPI: WMI: Mapper loaded
Apr  2 23:43:43 jack-desktop kernel: [   23.059960] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4800+ processors (2 cpu cores) (version 2.20.00)
Apr  2 23:43:43 jack-desktop kernel: [   23.759402] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Apr  2 23:43:43 jack-desktop kernel: [   24.054846] NET: Registered protocol family 10
Apr  2 23:43:43 jack-desktop kernel: [   24.056717] lo: Disabled Privacy Extensions
Apr  2 23:43:44 jack-desktop kernel: [   24.439360] ppdev: user-space parallel port driver
Apr  2 23:43:48 jack-desktop kernel: [   28.884777] VBoxDrv: dbg - g_abExecMemory=ffffffffa0705fe0
Apr  2 23:43:48 jack-desktop kernel: [   28.884797] vboxdrv: fAsync=1 offMin=0x10af93 offMax=0x10af93
Apr  2 23:43:48 jack-desktop kernel: [   28.887123] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
Apr  2 23:43:48 jack-desktop kernel: [   29.096451] VBoxNetFlt: dbg - g_abExecMemory=ffffffffa08a3e20
Apr  2 23:43:49 jack-desktop kernel: [   30.161648] Bluetooth: Core ver 2.13
Apr  2 23:43:49 jack-desktop kernel: [   30.162273] NET: Registered protocol family 31
Apr  2 23:43:49 jack-desktop kernel: [   30.162276] Bluetooth: HCI device and connection manager initialized
Apr  2 23:43:49 jack-desktop kernel: [   30.162281] Bluetooth: HCI socket layer initialized
Apr  2 23:43:49 jack-desktop kernel: [   30.173386] Bluetooth: L2CAP ver 2.11
Apr  2 23:43:49 jack-desktop kernel: [   30.173394] Bluetooth: L2CAP socket layer initialized
Apr  2 23:43:49 jack-desktop kernel: [   30.183810] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Apr  2 23:43:49 jack-desktop kernel: [   30.183815] Bluetooth: BNEP filters: protocol multicast
Apr  2 23:43:49 jack-desktop kernel: [   30.208159] Bridge firewalling registered
Apr  2 23:43:49 jack-desktop kernel: [   30.218084] Bluetooth: SCO (Voice Link) ver 0.6
Apr  2 23:43:49 jack-desktop kernel: [   30.218090] Bluetooth: SCO socket layer initialized
Apr  2 23:43:50 jack-desktop kernel: [   30.270182] Bluetooth: RFCOMM socket layer initialized
Apr  2 23:43:50 jack-desktop kernel: [   30.270550] Bluetooth: RFCOMM TTY layer initialized
Apr  2 23:43:50 jack-desktop kernel: [   30.270554] Bluetooth: RFCOMM ver 1.10
Apr  2 23:43:54 jack-desktop kernel: [   34.357412] skge eth1: enabling interface
Apr  2 23:43:54 jack-desktop kernel: [   34.361170] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr  2 23:43:54 jack-desktop kernel: [   34.362543] sky2 eth0: enabling interface
Apr  2 23:43:54 jack-desktop kernel: [   34.364993] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr  2 23:43:54 jack-desktop kernel: [   34.477172] NET: Registered protocol family 17
Apr  2 23:43:55 jack-desktop kernel: [   35.452333] [fglrx] CMM init INV FB MC:0xd0000000, length:0x10000000
Apr  2 23:43:55 jack-desktop kernel: [   35.452345] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Apr  2 23:43:55 jack-desktop kernel: [   35.452347] [fglrx] Reserved FB block: Unshared offset:7ffb000, size:5000 
Apr  2 23:43:55 jack-desktop kernel: [   35.452350] [fglrx] Reserved FB block: Unshared offset:ffbc000, size:44000 
Apr  2 23:44:00 jack-desktop kernel: [   40.702251] skge eth1: Link is up at 100 Mbps, full duplex, flow control both
Apr  2 23:44:00 jack-desktop kernel: [   40.702819] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Apr  3 00:03:44 jack-desktop -- MARK --
Apr  3 00:23:44 jack-desktop -- MARK --
Apr  3 08:59:18 jack-desktop syslogd 1.5.0#2ubuntu6: restart.
Apr  3 08:59:18 jack-desktop kernel: Inspecting /boot/System.map-2.6.27-11-generic


```

The computer was fine when I went to sleep. When I woke up it was off.

---

### Post by europa on 2009-04-05
bump

---

### Post by europa on 2009-04-12
Just Give Me the Beans!

---

### Post by isutoshi on 2009-04-12
The exact same thing happened on my Windows box. I was told the only solution was to upgrade the BIOS firmware, but before I had a chance to try that, the graphics card fried. Waiting for a replacement now...

So I guess you should try that: update your BIOS firmware.

---

### Post by europa on 2009-04-13
> **isutoshi said:**
> The exact same thing happened on my Windows box. I was told the only solution was to upgrade the BIOS firmware, but before I had a chance to try that, the graphics card fried. Waiting for a replacement now...

So I guess you should try that: update your BIOS firmware.

I think that hte fact that your graphics card fried is kind of a dead giveaway that the video card was the problem.  It was mentioned earlier in the thread.

I'll have to take a look at this card. if it's going bad i'm going to be hella pissed.

---

### Post by europa on 2009-04-16
I took a closer look at my video card.

I have an ati radeon x9500.  It is a 2 slot card (one for the card, one for the vent).  I took a look inside the vent and found dust that, when pulled out in one piece, was 3 inches long and half a centimeter thick.

Computer has been running fine for 3 days now.

---

