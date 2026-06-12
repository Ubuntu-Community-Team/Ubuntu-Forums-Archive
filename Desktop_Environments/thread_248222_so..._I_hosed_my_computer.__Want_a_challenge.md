---
title: "so... I hosed my computer.  Want a challenge?"
date: 2006-08-31
forum: Desktop Environments
---

### Post by loopjeremyloop on 2006-08-31
HOKAY.
Here's my system setup, as it was before I hosed it:

dev/hda1 = windows XP (hda=30 gig drive)
dev/hdb1 = large NTFS partition (140 of 160 gigs)
dev/hdb2 = ubuntu partition (19 of 160)
dev/hdb5 = swap

I decided that I needed to upgrade my drive space from the 20 gig partition to use the rest of my 160 gig drive, but you can't resize ext3 from the back to the front - since the ext3 partition resided at the end of my drive, my only choice was to pull the data from the partition, repartition, and then put the data back on.

SO...
I followed a good amount of this thread:
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

I backed up my data, threw it on another system, booted to the ubuntu livecd and blew out the drive partitions for hdab1 and hdb2.  I then created a partition and formatted it as ext3 (hdb1).

As root, i then untarred my file in the right spot after mounting this drive and then verified that the folders were all there. I recreated lost and found, sys, and tmp and added the right permissions (777, sticky on tmp).  so far so good.

Next, I ran grub to replace the MBR and point it at hd(1,0) instead of hd(1,1) and then edited my fstab and menu.lst to point all in the right places.

Then I went and smoked some crack, apparently, while the system rebooted.


The system goes through the "loading drivers" etc splashscreen with teh wonderful brown color just wonderfully.  after a short pause, it drops to a terminal screen where the following text occurs:
(i'm going to type in a few of the lines by hand)
```

 *preparing restricted drivers...
ld_static: cannot open output file /lib/modules/2.6.15-26-686/volatile/ath_hal.ko: Read-only file system
ld_static: cannot open output file /lib/modules/2.6.15-26-686/volatile/fcdsl.ko: Read-only file system
ld_static: cannot open output file /lib/modules/2.6.15-26-686/volatile/fcdsl2.ko:  Read-only file system
ld_static: cannot open output file /lib/modules/2.6.15-26-686/volatile/fcdslsl.ko:  Read-only file system
ld_static: cannot open output file /lib/modules/2.6.15-26-686/volatiledcdslslusb.ko:  Read-only file system

```

there are about 7 more lines after that, all in the same directory.

at this point, the cursor sits blinking at the bottom of the screen... 

If I hit ctrl-alt-1 2 3 4, I can go to those terminals.... and login as my USERname that I had in the last installation - but no sudo, no root.  those passwords seem to be lost.  I also can't RUN ANYTHING.  the files are ALL there, but they're all unusable.

Any thoughts on how to fix this system?

Reinstall, while fun, is my last resort.  Thanks in advance!

---

### Post by mssever on 2006-08-31
To repair your system, you can either use recovery mode (preferred) or mount your partition from a live CD.

The first thing I would do is look in /var/log/dmesg for errors. By default, Ubuntu has the following option in /etc/fstab for the root partition: errors=remount-ro. This suggests that there is an error somewhere that caused the kernel to switch your root partition to read-only to prevent further hosing your system.

If you're in recovery mode, you can try ```
mount #see if your root partition has ro next to it. If so, continue
mount -o remount,rw /
telinit 5
``` Of course, this doesn't fix your problem, but it does confirm that the partition is being mounted ro. And it should give you either a functional system from which to fix whatever the problem is, or give you some new errors which might help pinpoint the problem. The various logs in /var/log are your friend.

---

### Post by loopjeremyloop on 2006-08-31
awesome, some great suggestions.  I feel a bit more confident about being able to fix it now....


will update in the morning from my office.


thanks!!!!

---

### Post by loopjeremyloop on 2006-09-01
okay... looking through my logs.  thank god my fstab still mounts a network share - cuz here's dmesg.  :)


```

[17179569.184000] Linux version 2.6.15-26-686 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Thu Aug 3 03:13:28 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000005ff70000 (usable)
[17179569.184000]  BIOS-e820: 000000005ff70000 - 000000005ff72000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000005ff72000 - 000000005ff93000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000005ff93000 - 0000000060000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fecf0000 - 00000000fecf1000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[17179569.184000] 639MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000fe710
[17179569.184000] On node 0 totalpages: 393072
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 163696 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 DELL                                  ) @ 0x000feba0
[17179569.184000] ACPI: RSDT (v001 DELL    GX270   0x00000008 ASL  0x00000061) @ 0x000fd196
[17179569.184000] ACPI: FADT (v001 DELL    GX270   0x00000008 ASL  0x00000061) @ 0x000fd1ce
[17179569.184000] ACPI: SSDT (v001   DELL    st_ex 0x00001000 MSFT 0x0100000d) @ 0xfffd526f
[17179569.184000] ACPI: MADT (v001 DELL    GX270   0x00000008 ASL  0x00000061) @ 0x000fd242
[17179569.184000] ACPI: BOOT (v001 DELL    GX270   0x00000008 ASL  0x00000061) @ 0x000fd2ae
[17179569.184000] ACPI: ASF! (v016 DELL    GX270   0x00000008 ASL  0x00000061) @ 0x000fd2d6
[17179569.184000] ACPI: DSDT (v001   DELL    dt_ex 0x00001000 MSFT 0x0100000d) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:2 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 15:2 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
[17179569.184000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 70000000 (gap: 60000000:9ec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hdb1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 2593.872 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179571.260000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179571.260000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.336000] Memory: 1545852k/1572288k available (2110k kernel code, 25240k reserved, 595k data, 332k init, 654784k highmem)
[17179571.336000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179571.416000] Calibrating delay using timer specific routine.. 5192.69 BogoMIPS (lpj=10385398)
[17179571.416000] Security Framework v1.0.0 initialized
[17179571.416000] SELinux:  Disabled at boot.
[17179571.416000] Mount-cache hash table entries: 512
[17179571.416000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[17179571.416000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[17179571.416000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179571.416000] CPU: L2 cache: 512K
[17179571.416000] CPU: Hyper-Threading is disabled
[17179571.416000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000 00000000
[17179571.416000] mtrr: v2.0 (20020519)
[17179571.416000] Enabling fast FPU save and restore... done.
[17179571.416000] Enabling unmasked SIMD FPU exception support... done.
[17179571.416000] Checking 'hlt' instruction... OK.
[17179571.432000] SMP alternatives: switching to UP code
[17179571.432000] checking if image is initramfs... it is
[17179571.936000] Freeing initrd memory: 6809k freed
[17179571.944000] ACPI: Looking for DSDT ... not found!
[17179571.968000] CPU0: Intel(R) Pentium(R) 4 CPU 2.60GHz stepping 09
[17179571.968000] SMP alternatives: switching to SMP code
[17179571.968000] Booting processor 1/1 eip 3000
[17179571.980000] Initializing CPU#1
[17179572.060000] Calibrating delay using timer specific routine.. 5187.46 BogoMIPS (lpj=10374936)
[17179572.060000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[17179572.060000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[17179572.060000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179572.060000] CPU: L2 cache: 512K
[17179572.060000] CPU: Hyper-Threading is disabled
[17179572.060000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000 00000000
[17179572.060000] CPU1: Intel(R) Pentium(R) 4 CPU 2.60GHz stepping 09
[17179572.060000] Total of 2 processors activated (10380.16 BogoMIPS).
[17179572.060000] ENABLING IO-APIC IRQs
[17179572.060000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179572.204000] checking TSC synchronization across 2 CPUs: passed.
[17179572.208000] Brought up 2 CPUs
[17179572.208000] NET: Registered protocol family 16
[17179572.208000] EISA bus registered
[17179572.208000] ACPI: bus type pci registered
[17179572.208000] PCI: PCI BIOS revision 2.10 entry at 0xfbab4, last bus=2
[17179572.208000] PCI: Using configuration type 1
[17179572.208000] ACPI: Subsystem revision 20051216
[17179572.244000] ACPI: Interpreter enabled
[17179572.244000] ACPI: Using IOAPIC for interrupt routing
[17179572.248000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179572.248000] PCI: Probing PCI hardware (bus 00)
[17179572.248000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179572.268000] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[17179572.268000] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[17179572.268000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179572.268000] Boot video device is 0000:01:00.0
[17179572.268000] PCI: Transparent bridge - 0000:00:1e.0
[17179572.268000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179572.432000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[17179572.448000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[17179572.448000] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 15)
[17179572.448000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[17179572.452000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[17179572.452000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[17179572.452000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[17179572.452000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[17179572.452000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[17179572.452000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179572.452000] pnp: PnP ACPI init
[17179572.484000] pnp: PnP ACPI: found 9 devices
[17179572.484000] PnPBIOS: Disabled by ACPI PNP
[17179572.484000] PCI: Using ACPI for IRQ routing
[17179572.484000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.504000] pnp: 00:08: ioport range 0x800-0x85f could not be reserved
[17179572.504000] pnp: 00:08: ioport range 0xc00-0xc7f has been reserved
[17179572.504000] pnp: 00:08: ioport range 0x860-0x8ff could not be reserved
[17179572.504000] PCI: Bridge: 0000:00:01.0
[17179572.504000]   IO window: d000-dfff
[17179572.504000]   MEM window: fe900000-feafffff
[17179572.504000]   PREFETCH window: e8000000-f7ffffff
[17179572.504000] PCI: Bridge: 0000:00:1e.0
[17179572.504000]   IO window: c000-cfff
[17179572.504000]   MEM window: fe800000-fe8fffff
[17179572.504000]   PREFETCH window: disabled.
[17179572.504000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179572.504000] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[17179572.504000] Simple Boot Flag at 0x7a set to 0x1
[17179572.504000] audit: initializing netlink socket (disabled)
[17179572.504000] audit(1157053175.500:1): initialized
[17179572.504000] highmem bounce pool size: 64 pages
[17179572.504000] VFS: Disk quotas dquot_6.5.1
[17179572.504000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.504000] Initializing Cryptographic API
[17179572.504000] io scheduler noop registered
[17179572.504000] io scheduler anticipatory registered
[17179572.504000] io scheduler deadline registered
[17179572.504000] io scheduler cfq registered
[17179572.504000] isapnp: Scanning for PnP cards...
[17179572.860000] isapnp: No Plug & Play device found
[17179572.880000] Real Time Clock Driver v1.12
[17179572.880000] PNP: No PS/2 controller found. Probing ports directly.
[17179572.884000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179572.884000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179572.884000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179572.884000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.888000] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.888000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179572.888000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.888000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179572.888000] mice: PS/2 mouse device common for all mice
[17179572.888000] EISA: Probing bus 0 at eisa.0
[17179572.888000] EISA: Detected 0 cards.
[17179572.888000] NET: Registered protocol family 2
[17179572.948000] IP route cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.948000] TCP established hash table entries: 262144 (order: 9, 3145728 bytes)
[17179572.948000] TCP bind hash table entries: 65536 (order: 7, 786432 bytes)
[17179572.952000] TCP: Hash tables configured (established 262144 bind 65536)
[17179572.952000] TCP reno registered
[17179572.952000] TCP bic registered
[17179572.952000] NET: Registered protocol family 1
[17179572.952000] NET: Registered protocol family 8
[17179572.952000] NET: Registered protocol family 20
[17179572.952000] Starting balanced_irq
[17179572.952000] Using IPI No-Shortcut mode
[17179572.952000] ACPI wakeup devices: 
[17179572.952000] VBTN PCI0 USB0 USB1 USB2 USB3 PCI1 
[17179572.952000] ACPI: (supports S0 S1 S3 S4 S5)
[17179572.952000] Freeing unused kernel memory: 332k freed
[17179573.012000] vga16fb: initializing
[17179573.012000] vga16fb: mapped to 0xc00a0000
[17179573.120000] Console: switching to colour frame buffer device 80x25
[17179573.120000] fb0: VGA16 VGA frame buffer device
[17179574.160000] Capability LSM initialized
[17179574.968000] ICH5: IDE controller at PCI slot 0000:00:1f.1
[17179574.968000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 169
[17179574.968000] ICH5: chipset revision 2
[17179574.968000] ICH5: not 100% native mode: will probe irqs later
[17179574.968000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
[17179574.968000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:DMA
[17179574.968000] Probing IDE interface ide0...
[17179575.264000] hda: WDC WD400BB-75FRA0, ATA DISK drive
[17179575.548000] hdb: ST3200822A, ATA DISK drive
[17179575.608000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179575.612000] Probing IDE interface ide1...
[17179576.352000] hdc: PLEXTOR DVDR PX-712A, ATAPI CD/DVD-ROM drive
[17179576.804000] hdd: _NEC CD-RW NR-9300A, ATAPI CD/DVD-ROM drive
[17179576.864000] ide1 at 0x170-0x177,0x376 on irq 15
[17179576.884000] hda: max request size: 1024KiB
[17179576.904000] hda: 78125000 sectors (40000 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[17179576.904000] hda: cache flushes supported
[17179576.904000]  hda: hda1
[17179576.916000] hdb: max request size: 1024KiB
[17179576.916000] hdb: 390721968 sectors (200049 MB) w/8192KiB Cache, CHS=24321/255/63, UDMA(100)
[17179576.916000] hdb: cache flushes supported
[17179576.916000]  hdb: hdb1 hdb3 < hdb5 >
[17179576.960000] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 8192kB Cache, UDMA(33)
[17179576.960000] Uniform CD-ROM driver Revision: 3.20
[17179576.964000] hdd: ATAPI 48X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179577.300000] SCSI subsystem initialized
[17179577.304000] ACPI: bus type scsi registered
[17179577.304000] libata version 1.20 loaded.
[17179577.304000] ata_piix 0000:00:1f.2: version 1.05
[17179577.304000] ata_pci_init_one: pci_dev class+intf: 0x1018f
[17179577.304000] ata_pci_init_one: NO_LEGACY == 0
[17179577.304000] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 169
[17179577.304000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179577.304000] ata1: PATA max UDMA/133 cmd 0xFE00 ctl 0xFE12 bmdma 0xFEA0 irq 169
[17179577.304000] ata2: PATA max UDMA/133 cmd 0xFE20 ctl 0xFE32 bmdma 0xFEA8 irq 169
[17179578.592000] scsi0 : ata_piix
[17179579.884000] scsi1 : ata_piix
[17179579.968000] usbcore: registered new driver usbfs
[17179579.968000] usbcore: registered new driver hub
[17179579.976000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 177
[17179579.976000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179579.976000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179579.976000] ehci_hcd 0000:00:1d.7: debug port 1
[17179579.976000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[17179579.976000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[17179579.976000] ehci_hcd 0000:00:1d.7: irq 177, io mem 0xffa80800
[17179579.976000] USB Universal Host Controller Interface driver v2.3
[17179579.976000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 185
[17179579.976000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179579.976000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179579.976000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[17179579.976000] uhci_hcd 0000:00:1d.0: irq 185, io base 0x0000ff80
[17179579.976000] hub 2-0:1.0: USB hub found
[17179579.976000] hub 2-0:1.0: 2 ports detected
[17179579.980000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179580.084000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 193
[17179580.084000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179580.084000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179580.084000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[17179580.084000] uhci_hcd 0000:00:1d.1: irq 193, io base 0x0000ff60
[17179580.084000] hub 3-0:1.0: USB hub found
[17179580.084000] hub 3-0:1.0: 2 ports detected
[17179580.188000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 169
[17179580.188000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179580.188000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179580.192000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[17179580.192000] uhci_hcd 0000:00:1d.2: irq 169, io base 0x0000ff40
[17179580.192000] hub 4-0:1.0: USB hub found
[17179580.192000] hub 4-0:1.0: 2 ports detected
[17179580.296000] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 185
[17179580.296000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179580.296000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179580.300000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[17179580.300000] uhci_hcd 0000:00:1d.3: irq 185, io base 0x0000ff20
[17179580.300000] hub 5-0:1.0: USB hub found
[17179580.300000] hub 5-0:1.0: 2 ports detected
[17179580.408000] hub 1-0:1.0: USB hub found
[17179580.408000] hub 1-0:1.0: 8 ports detected
[17179580.644000] Attempting manual resume
[17179580.656000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179580.656000] EXT3-fs: write access will be enabled during recovery.
[17179581.076000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[17179581.108000] EXT3-fs: recovery complete.
[17179581.108000] kjournald starting.  Commit interval 5 seconds
[17179581.124000] EXT3-fs: mounted filesystem with ordered data mode.
[17179586.600000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179586.608000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179586.700000] Linux agpgart interface v0.101 (c) Dave Jones
[17179586.704000] agpgart: Detected an Intel 865 Chipset.
[17179586.708000] agpgart: AGP aperture is 128M @ 0xe0000000
[17179586.836000] hw_random hardware driver 1.0.0 loaded
[17179586.856000] usbcore: registered new driver hiddev
[17179586.864000] input: Logitech USB Receiver as /class/input/input0
[17179586.864000] input: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.0-1
[17179586.876000] input: Logitech USB Receiver as /class/input/input1
[17179586.876000] input,hiddev96: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1
[17179586.876000] usbcore: registered new driver usbhid
[17179586.876000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179587.244000] Intel(R) PRO/1000 Network Driver - version 7.0.33-k2
[17179587.244000] Copyright (c) 1999-2005 Intel Corporation.
[17179587.244000] ACPI: PCI Interrupt 0000:02:0c.0[A] -> GSI 18 (level, low) -> IRQ 169
[17179587.312000] Floppy drive(s): fd0 is 1.44M
[17179587.324000] input: PC Speaker as /class/input/input2
[17179587.332000] FDC 0 is a post-1991 82077
[17179587.376000] parport: PnPBIOS parport detected.
[17179587.380000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[17179587.544000] ts: Compaq touchscreen protocol output
[17179587.652000] e1000: 0000:02:0c.0: e1000_probe: (PCI:33MHz:32-bit) 00:0b:db:77:99:01
[17179587.692000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[17179587.920000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 201
[17179587.920000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179588.240000] intel8x0_measure_ac97_clock: measured 58328 usecs
[17179588.240000] intel8x0: clocking to 48000
[17179588.464000] lp0: using parport0 (interrupt-driven).
[17179588.580000] Adding 2080376k swap on /dev/hdb5.  Priority:-1 extents:1 across:2080376k
[17179588.640000] EXT3 FS on hdb1, internal journal
[17179588.824000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179588.824000] md: bitmap version 4.39
[17179589.072000] NET: Registered protocol family 17
[17179589.336000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179589.652000] cdrom: open failed.
[17179589.996000] cdrom: open failed.
[17179590.000000] cdrom: open failed.
[17179590.904000] e1000: eth0: e1000_watchdog_task: NIC Link is Up 1000 Mbps Full Duplex

```

what other logs are worth having here?  I'm reading through it, not seeing what I need to see though.... or rather, nothing obvious is showing up.

oh, and i can't remount the drive, as I can't access root!
[edit - yes, i can remount the drive... but root is still inaccessable to me.  argh.]

---

### Post by loopjeremyloop on 2006-09-01
well now.  holy cow. 


looks like the archive might have been corrupt. 


ARGH.





okay.  looking for the original dvd i burned it to now.... :/


EDIT:

ignore it all.  reinstalling.  f. it.  


:/

---

### Post by mssever on 2006-09-01
Sorry it didn't work out for you. You would have had root access from recovery mode, but that wouldn't have identified that problem. Reinstalling may well be the best option.

---

