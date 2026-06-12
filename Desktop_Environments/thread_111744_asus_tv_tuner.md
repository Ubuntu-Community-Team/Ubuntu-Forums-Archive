---
title: "asus tv tuner"
date: 2006-01-02
forum: Desktop Environments
---

### Post by veratyr on 2006-01-02
Trying to get my tv card (Asus tv880) working in breezy. The card has a cx23880 chip. HELP!

lspci output

```
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
0000:00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
0000:00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
0000:00:0a.0 Multimedia video controller: Conexant Winfast TV2000 XP (rev 03)
0000:00:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
0000:00:0b.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 07)
0000:00:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR] (rev b2)
```

lsmod output

```
Module                  Size  Used by
rfcomm                 40600  0
l2cap                  27840  5 rfcomm
bluetooth              51364  4 rfcomm,l2cap
speedstep_lib           4548  0
cpufreq_userspace       6208  0
cpufreq_stats           6080  0
freq_table              4736  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        7208  0
cpufreq_conservative     8140  0
nvidia               3713060  12
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5548  0
pcc_acpi               11360  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5696  0
button                  6704  0
battery                 9572  0
container               4608  0
ac                      4932  0
ipv6                  264000  8
af_packet              23656  2
floppy                 60564  0
pcspkr                  3880  0
rtc                    13672  0
emu10k1_gp              3872  0
gameport               16200  2 emu10k1_gp
snd_emu10k1_synth       8032  0
snd_emux_synth         37664  1 snd_emu10k1_synth
snd_seq_virmidi         7872  1 snd_emux_synth
snd_seq_midi_emul       7808  1 snd_emux_synth
snd_emu10k1           121604  2 snd_emu10k1_synth
snd_ac97_codec         84508  1 snd_emu10k1
snd_pcm_oss            53760  0
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                92900  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10824  2 snd_emu10k1,snd_pcm
snd_util_mem            4672  2 snd_emux_synth,snd_emu10k1
snd_hwdep               9248  2 snd_emux_synth,snd_emu10k1
tuner                  27336  0
cx8800                 32588  0
cx88xx                 54368  1 cx8800
i2c_algo_bit            9640  1 cx88xx
video_buf              21764  2 cx8800,cx88xx
ir_common               7620  1 cx88xx
tveeprom               13336  1 cx88xx
v4l1_compat            14916  1 cx8800
v4l2_common             5952  1 cx8800
btcx_risc               5096  2 cx8800,cx88xx
videodev                9760  2 cx8800,cx88xx
i2c_viapro              8208  0
via686a                20088  0
i2c_sensor              3584  1 via686a
i2c_core               21760  8 i2c_acpi_ec,tuner,cx88xx,i2c_algo_bit,tveeprom,i2c_viapro,via686a,i2c_sensor
shpchp                 97860  0
pci_hotplug            28412  1 shpchp
via_agp                 9888  1
agpgart                35436  2 nvidia,via_agp
dm_mod                 59232  1
tsdev                   8000  0
piix                   10980  0
snd_seq_dummy           3844  0
evdev                   9920  0
snd_seq_oss            34976  0
snd_seq_midi            9344  0
snd_rawmidi            25952  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      7392  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                55280  10 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              25956  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          8716  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    57764  16 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10176  1 snd
psmouse                30628  0
mousedev               12132  1
parport_pc             36356  1
lp                     12548  0
parport                37384  2 parport_pc,lp
md                     47536  0
ext3                  138824  1
jbd                    59768  1 ext3
mbcache                10116  1 ext3
thermal                13320  0
processor              23816  1 thermal
fan                     4708  0
3c59x                  42280  0
mii                     5920  1 3c59x
uhci_hcd               32720  0
usbcore               121308  2 uhci_hcd
ide_cd                 42148  0
cdrom                  40096  1 ide_cd
ide_disk               18880  3
ide_generic             1600  0
via82cxxx              13724  1
ide_core              140628  5 piix,ide_cd,ide_disk,ide_generic,via82cxxx
unix                   29392  640
vesafb                  8216  0
capability              4936  0
commoncap               7040  1 capability
vga16fb                12840  1
vgastate                9888  1 vga16fb
softcursor              2496  2 vesafb,vga16fb
cfbimgblt               3168  2 vesafb,vga16fb
cfbfillrect             4096  2 vesafb,vga16fb
cfbcopyarea             4832  2 vesafb,vga16fb
fbcon                  38880  72
tileblit                2592  1 fbcon
font                    8448  1 fbcon
bitblit                 5856  1 fbcon
```

dmesg output

```
[4294667.296000] Linux version 2.6.12-10-686-smp (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 SMP Thu Dec 22 12:13:35 UTC 2005
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[4294667.296000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000dc000 - 00000000000e0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 0000000017ff0000 (usable)
[4294667.296000]  BIOS-e820: 0000000017ff0000 - 0000000017ff8000 (ACPI data)
[4294667.296000]  BIOS-e820: 0000000017ff8000 - 0000000018000000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[4294667.296000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 383MB LOWMEM available.
[4294667.296000] found SMP MP-table at 000fb100
[4294667.296000] On node 0 totalpages: 98288
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:1
[4294667.296000]   Normal zone: 94192 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:1
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 AMI                                   ) @ 0x000fc590
[4294667.296000] ACPI: RSDT (v001 AMIINT VIA_694X 0x00000010 MSFT 0x00000099) @ 0x17ff0000
[4294667.296000] ACPI: FADT (v001 AMIINT VIA_694X 0x00000011 MSFT 0x00000099) @ 0x17ff0030
[4294667.296000] ACPI: MADT (v001 AMIINT          0x00000009 MSFT 0x00000099) @ 0x17ff00b0
[4294667.296000] ACPI: DSDT (v001    VIA APOLLO-P 0x00001000 MSFT 0x0100000b) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x808
[4294667.296000] ACPI: Local APIC address 0xfee00000
[4294667.296000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[4294667.296000] Processor #0 6:8 APIC version 17
[4294667.296000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[4294667.296000] Processor #1 6:8 APIC version 17
[4294667.296000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[4294667.296000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[4294667.296000] ACPI: IRQ0 used by override.
[4294667.296000] ACPI: IRQ2 used by override.
[4294667.296000] ACPI: IRQ9 used by override.
[4294667.296000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[4294667.296000] Using ACPI (MADT) for SMP configuration information
[4294667.296000] Allocating PCI resources starting at 18000000 (gap: 18000000:e6c00000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[4294667.296000] Detected 864.015 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294668.509000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294668.510000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294668.552000] Memory: 380268k/393152k available (1723k kernel code, 12268k reserved, 740k data, 204k init, 0k highmem)[4294668.552000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294668.553000] Calibrating delay loop... 1708.03 BogoMIPS (lpj=854016)
[4294668.576000] Security Framework v1.0.0 initialized
[4294668.576000] SELinux:  Disabled at boot.
[4294668.576000] Mount-cache hash table entries: 512
[4294668.576000] CPU: After generic identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000 00000000
[4294668.576000] CPU: After vendor identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000 00000000
[4294668.576000] CPU: L1 I cache: 16K, L1 D cache: 16K
[4294668.576000] CPU: L2 cache: 256K
[4294668.576000] CPU: After all inits, caps: 0383fbff 00000000 00000000 00000040 00000000 00000000 00000000
[4294668.576000] Intel machine check architecture supported.
[4294668.576000] Intel machine check reporting enabled on CPU#0.
[4294668.576000] Enabling fast FPU save and restore... done.
[4294668.576000] Enabling unmasked SIMD FPU exception support... done.
[4294668.576000] Checking 'hlt' instruction... OK.
[4294668.580000] checking if image is initramfs... it is
[4294669.643000] Freeing initrd memory: 5568k freed
[4294669.646000] ACPI: Looking for DSDT in initrd... not found!
[4294669.813000]  not found!
[4294669.825000] CPU0: Intel Pentium III (Coppermine) stepping 0a
[4294669.825000] Booting processor 1/1 eip 3000
[4294669.835000] Initializing CPU#1
[4294669.836000] Calibrating delay loop... 1724.41 BogoMIPS (lpj=862208)
[4294669.858000] CPU: After generic identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000 00000000
[4294669.858000] CPU: After vendor identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000 00000000
[4294669.858000] CPU: L1 I cache: 16K, L1 D cache: 16K
[4294669.858000] CPU: L2 cache: 256K
[4294669.858000] CPU: After all inits, caps: 0383fbff 00000000 00000000 00000040 00000000 00000000 00000000
[4294669.858000] Intel machine check architecture supported.
[4294669.858000] Intel machine check reporting enabled on CPU#1.
[4294669.858000] CPU1: Intel Pentium III (Coppermine) stepping 0a
[4294669.858000] Total of 2 processors activated (3432.44 BogoMIPS).
[4294669.858000] ENABLING IO-APIC IRQs
[4294669.858000] ..TIMER: vector=0x31 pin1=2 pin2=-1
[4294669.969000] checking TSC synchronization across 2 CPUs: passed.
[4294669.970000] Brought up 2 CPUs
[4294669.970000] CPU0 attaching sched-domain:
[4294669.970000]  domain 0: span 01
[4294669.970000]   groups: 01
[4294669.970000]   domain 1: span 03
[4294669.970000]    groups: 01 02
[4294669.970000] CPU1 attaching sched-domain:
[4294669.970000]  domain 0: span 02
[4294669.970000]   groups: 02
[4294669.970000]   domain 1: span 03
[4294669.970000]    groups: 02 01
[4294669.971000] NET: Registered protocol family 16
[4294669.971000] ACPI: bus type pci registered
[4294669.972000] PCI: PCI BIOS revision 2.10 entry at 0xfdb01, last bus=1
[4294669.972000] PCI: Using configuration type 1
[4294669.972000] mtrr: v2.0 (20020519)
[4294669.972000] mtrr: your CPUs had inconsistent variable MTRR settings
[4294669.972000] mtrr: probably your BIOS does not setup all CPUs.
[4294669.972000] mtrr: corrected configuration.
[4294669.973000] ACPI: Subsystem revision 20050729
[4294669.986000] ACPI: Interpreter enabled
[4294669.986000] ACPI: Using IOAPIC for interrupt routing
[4294669.987000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294669.987000] PCI: Probing PCI hardware (bus 00)
[4294669.987000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294669.990000] Boot video device is 0000:01:00.0
[4294669.993000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294669.995000] ACPI: Power Resource [URP1] (off)
[4294669.995000] ACPI: Power Resource [URP2] (off)
[4294669.995000] ACPI: Power Resource [FDDP] (off)
[4294669.995000] ACPI: Power Resource [LPTP] (off)
[4294670.000000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[4294670.001000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[4294670.001000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
[4294670.002000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[4294670.002000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294670.002000] pnp: PnP ACPI init
[4294670.008000] pnp: PnP ACPI: found 10 devices
[4294670.008000] PnPBIOS: Disabled by ACPI PNP
[4294670.008000] PCI: Using ACPI for IRQ routing
[4294670.008000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294670.033000] audit: initializing netlink socket (disabled)
[4294670.033000] audit: initialized
[4294670.034000] VFS: Disk quotas dquot_6.5.1
[4294670.034000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294670.034000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294670.034000] devfs: boot_options: 0x0
[4294670.034000] Initializing Cryptographic API
[4294670.034000] PCI: Enabling Via external APIC routing
[4294670.034000] isapnp: Scanning for PnP cards...
[4294670.388000] isapnp: No Plug & Play device found
[4294670.437000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[4294670.437000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294670.437000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294670.437000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294670.437000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294670.438000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294670.443000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294670.443000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294670.443000] io scheduler noop registered
[4294670.443000] io scheduler anticipatory registered
[4294670.443000] io scheduler deadline registered
[4294670.443000] io scheduler cfq registered
[4294670.444000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294670.445000] NET: Registered protocol family 2
[4294670.459000] IP: routing cache hash table of 4096 buckets, 32Kbytes
[4294670.459000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[4294670.460000] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[4294670.460000] TCP: Hash tables configured (established 16384 bind 16384)
[4294670.460000] NET: Registered protocol family 8
[4294670.461000] NET: Registered protocol family 20
[4294670.461000] ACPI wakeup devices:
[4294670.461000] PCI0 UAR1 UAR2  USB USB1
[4294670.461000] ACPI: (supports S0 S1 S4 S5)
[4294670.461000] Freeing unused kernel memory: 204k freed
[4294670.469000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294670.509000] vga16fb: initializing
[4294670.509000] vga16fb: mapped to 0xc00a0000
[4294670.635000] Console: switching to colour frame buffer device 80x30
[4294670.635000] fb0: VGA16 VGA frame buffer device
[4294671.731000] Capability LSM initialized
[4294671.761000] NET: Registered protocol family 1
[4294671.793000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.793000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294671.793000] ACPI: bus type ide registered
[4294671.812000] VP_IDE: IDE controller at PCI slot 0000:00:07.1
[4294671.812000] PCI: Via IRQ fixup for 0000:00:07.1, from 255 to 0
[4294671.812000] VP_IDE: chipset revision 6
[4294671.812000] VP_IDE: not 100% native mode: will probe irqs later
[4294671.812000] VP_IDE: VIA vt82c686b (rev 40) IDE UDMA100 controller on pci0000:00:07.1
[4294671.812000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[4294671.812000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:pio
[4294671.812000] Probing IDE interface ide0...
[4294672.198000] hda: WDC WD2000JB-19GVC0, ATA DISK drive
[4294672.813000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294672.813000] Probing IDE interface ide1...
[4294673.607000] hdc: Pioneer DVD-ROM ATAPIModel DVD-116 0122, ATAPI CD/DVD-ROM drive
[4294673.914000] ide1 at 0x170-0x177,0x376 on irq 15
[4294673.914000] Probing IDE interface ide2...
[4294674.427000] Probing IDE interface ide3...
[4294674.940000] Probing IDE interface ide4...
[4294675.453000] Probing IDE interface ide5...
[4294675.977000] hda: max request size: 1024KiB
[4294676.007000] hda: 390721968 sectors (200049 MB) w/8192KiB Cache, CHS=24321/255/63, UDMA(100)
[4294676.009000] hda: cache flushes supported
[4294676.009000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[4294676.075000] hdc: ATAPI 40X DVD-ROM drive, 256kB Cache
[4294676.075000] Uniform CD-ROM driver Revision: 3.20
[4294676.810000] Attempting manual resume
[4294676.817000] swsusp: Suspend partition has wrong signature?
[4294676.923000] usbcore: registered new driver usbfs
[4294676.923000] usbcore: registered new driver hub
[4294676.927000] USB Universal Host Controller Interface driver v2.2
[4294676.927000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[4294676.927000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[4294676.927000] uhci_hcd 0000:00:07.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
[4294676.990000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[4294676.990000] uhci_hcd 0000:00:07.2: irq 10, io base 0x0000d400
[4294676.990000] hub 1-0:1.0: USB hub found
[4294676.990000] hub 1-0:1.0: 2 ports detected
[4294676.993000] ACPI: PCI Interrupt 0000:00:07.3[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[4294676.993000] uhci_hcd 0000:00:07.3: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
[4294677.055000] uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2
[4294677.055000] uhci_hcd 0000:00:07.3: irq 10, io base 0x0000d800
[4294677.056000] hub 2-0:1.0: USB hub found
[4294677.056000] hub 2-0:1.0: 2 ports detected
[4294677.167000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294677.167000] 3c59x: Donald Becker and others. www.scyld.com/network/vortex.html
[4294677.167000] 0000:00:0c.0: 3Com PCI 3c905C Tornado at 0xcc00. Vers LK1.1.19
[4294680.020000] ACPI: CPU0 (power states: C1[C1])
[4294680.020000] ACPI: CPU1 (power states: C1[C1])
[4294680.024000] ACPI: Thermal Zone [THRM] (30 C)
[4294680.233000] Attempting manual resume
[4294680.270000] swsusp: Suspend partition has wrong signature?
[4294680.345000] EXT3-fs: INFO: recovery required on readonly filesystem.
[4294680.345000] EXT3-fs: write access will be enabled during recovery.
[4294681.825000] kjournald starting.  Commit interval 5 seconds
[4294681.825000] EXT3-fs: hda1: orphan cleanup on readonly fs
[4294681.825000] ext3_orphan_cleanup: deleting unreferenced inode 15171594
[4294681.825000] ext3_orphan_cleanup: deleting unreferenced inode 15171593
[4294681.825000] ext3_orphan_cleanup: deleting unreferenced inode 15171592
[4294681.825000] EXT3-fs: hda1: 3 orphan inodes deleted
[4294681.825000] EXT3-fs: recovery complete.
[4294681.834000] EXT3-fs: mounted filesystem with ordered data mode.
[4294682.973000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294687.946000] Adding 1132540k swap on /dev/hda5.  Priority:-1 extents:1
[4294688.208000] EXT3 FS on hda1, internal journal
[4294693.752000] parport_pc: VIA 686A/8231 detected
[4294693.752000] parport_pc: probing current configuration
[4294693.752000] parport_pc: Current parallel port base: 0x378
[4294693.752000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[4294693.835000] parport_pc: VIA parallel port: io=0x378, irq=7
[4294693.842000] lp0: using parport0 (interrupt-driven).
[4294693.880000] mice: PS/2 mouse device common for all mice
[4294694.207000] input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
[4294694.818000] ts: Compaq touchscreen protocol output
[4294697.708000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294698.598000] cdrom: open failed.
[4294701.145000] Linux agpgart interface v0.101 (c) Dave Jones
[4294701.154000] agpgart: Detected VIA Apollo Pro 133 chipset
[4294701.171000] agpgart: AGP aperture is 128M @ 0xe0000000
[4294701.387000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294701.400000] shpchp: shpc_init : shpc_cap_offset == 0
[4294701.400000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294702.519000] Linux video capture interface: v1.00
[4294702.598000] cx2388x v4l2 driver version 0.0.4 loaded
[4294702.601000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 18
[4294702.601000] cx88[0]: Your board isn't known (yet) to the driver.  You can
[4294702.601000] cx88[0]: try to pick one of the existing card configs via
[4294702.601000] cx88[0]: card=<n> insmod option.  Updating to the latest
[4294702.601000] cx88[0]: version might help as well.
[4294702.601000] cx88[0]: Here is a list of valid choices for the card=<n> insmod option:
[4294702.601000] cx88[0]:    card=0 -> UNKNOWN/GENERIC
[4294702.601000] cx88[0]:    card=1 -> Hauppauge WinTV 34xxx models
[4294702.601000] cx88[0]:    card=2 -> GDI Black Gold
[4294702.601000] cx88[0]:    card=3 -> PixelView
[4294702.601000] cx88[0]:    card=4 -> ATI TV Wonder Pro
[4294702.601000] cx88[0]:    card=5 -> Leadtek Winfast 2000XP Expert
[4294702.601000] cx88[0]:    card=6 -> AverTV Studio 303 (M126)
[4294702.601000] cx88[0]:    card=7 -> MSI TV-@nywhere Master
[4294702.601000] cx88[0]:    card=8 -> Leadtek Winfast DV2000
[4294702.601000] cx88[0]:    card=9 -> Leadtek PVR 2000
[4294702.601000] cx88[0]:    card=10 -> IODATA GV-VCP3/PCI
[4294702.601000] cx88[0]:    card=11 -> Prolink PlayTV PVR
[4294702.601000] cx88[0]:    card=12 -> ASUS PVR-416
[4294702.601000] cx88[0]:    card=13 -> MSI TV-@nywhere
[4294702.601000] cx88[0]:    card=14 -> KWorld/VStream XPert DVB-T
[4294702.601000] cx88[0]:    card=15 -> DVICO FusionHDTV DVB-T1
[4294702.601000] cx88[0]:    card=16 -> KWorld LTV883RF
[4294702.601000] cx88[0]:    card=17 -> DViCO - FusionHDTV 3 Gold
[4294702.601000] cx88[0]:    card=18 -> Hauppauge Nova-T DVB-T
[4294702.601000] cx88[0]:    card=19 -> Conexant DVB-T reference design
[4294702.601000] cx88[0]:    card=20 -> Provideo PV259
[4294702.601000] cx88[0]:    card=21 -> DVICO FusionHDTV DVB-T Plus
[4294702.601000] cx88[0]:    card=22 -> pcHDTV HD3000 HDTV
[4294702.601000] cx88[0]:    card=23 -> digitalnow DNTV Live! DVB-T
[4294702.601000] cx88[0]:    card=24 -> Hauppauge WinTV 28xxx (Roslyn) models
[4294702.601000] cx88[0]:    card=25 -> Digital-Logic MICROSPACE Entertainment Center (MEC)
[4294702.601000] cx88[0]:    card=26 -> IODATA GV/BCTV7E
[4294702.601000] cx88[0]: subsystem: 1043:4820, board: UNKNOWN/GENERIC [card=0,autodetected]
[4294702.767000] cx88[0]/0: found at 0000:00:0a.0, rev: 3, irq: 18, latency: 64, mmio: 0xdf000000
[4294702.800000] tuner 1-0060: chip found @ 0xc0 (cx88[0])
[4294702.839000] cx88[0]/0: registered device video0 [v4l2]
[4294702.849000] cx88[0]/0: registered device vbi0
[4294703.163000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 19
[4294704.152000] gameport: EMU10K1 is pci0000:00:0b.1/gameport0, io 0xdc00, speed 1269kHz
[4294705.616000] Real Time Clock Driver v1.12
[4294705.723000] input: PC Speaker
[4294706.142000] Floppy drive(s): fd0 is 1.44M
[4294706.158000] FDC 0 is a post-1991 82077
[4294707.370000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294707.396000] NET: Registered protocol family 17
[4294711.728000] NET: Registered protocol family 10
[4294711.728000] Disabled Privacy Extensions on device c0338fa0(lo)
[4294711.728000] IPv6 over IPv4 tunneling driver
[4294713.292000] ACPI: Power Button (FF) [PWRF]
[4294713.292000] ACPI: Power Button (CM) [PWRB]
[4294713.292000] ACPI: Sleep Button (CM) [SLPB]
[4294713.515000] ibm_acpi: ec object not found
[4294718.896000] nvidia: module license 'NVIDIA' taints kernel.
[4294718.913000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294718.913000] NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7667  Fri Jun 17 07:01:04 PDT 2005
[4294719.255000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4294719.255000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[4294719.255000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[4294721.780000] eth0: no IPv6 routers present
[4294722.092000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4294722.092000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 0x mode
[4294722.092000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 0x mode
[4294726.804000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294726.804000] apm: disabled - APM is not SMP safe.
[4294731.289000] Bluetooth: Core ver 2.7
[4294731.289000] NET: Registered protocol family 31
[4294731.289000] Bluetooth: HCI device and connection manager initialized
[4294731.289000] Bluetooth: HCI socket layer initialized
[4294731.319000] Bluetooth: L2CAP ver 2.7
[4294731.319000] Bluetooth: L2CAP socket layer initialized
[4294731.353000] Bluetooth: RFCOMM ver 1.5
[4294731.353000] Bluetooth: RFCOMM socket layer initialized
[4294731.354000] Bluetooth: RFCOMM TTY layer initialized
```

---

### Post by crispy_420 on 2006-01-03
The driver is called cx88. I personally don't have on card on that chipset (bt878 here). But maybe that will help narrow your search.

I read here the should be built in kernal support now (>2.6).

[http://linux.bytesex.org/v4l2/cx88.html]("http://linux.bytesex.org/v4l2/cx88.html")

Support Devices:

[http://linuxtv.org/v4lwiki/index.php/Cx88_devices_%28cx2388x%29]("http://linuxtv.org/v4lwiki/index.php/Cx88_devices_%28cx2388x%29")

Driver Download:

[http://dl.bytesex.org/releases/video4linux/]("http://dl.bytesex.org/releases/video4linux/")

Random LInks:

[http://www.linuxcompatible.org/Kword_TV_tuner_with_MythTv_t1170.html]("http://www.linuxcompatible.org/Kword_TV_tuner_with_MythTv_t1170.html")

[http://ubuntuforums.org/archive/index.php/t-75361.html]("http://ubuntuforums.org/archive/index.php/t-75361.html")

But from what I have seen, things don't look promising. I bought a card on the same chipset from KWorld and I think I never got it to work in linux. (maybe after a lot of work in FC3).

Look into a bt878 card. Works out of the box after one minor tweak to a config file. The TVTime site mentions it as channels off by one and color dull but that is only a NTSC (USA only). On the downside they are getting rare. Everyone moving toward that cx88 chipset.

---

### Post by endangst on 2006-01-03
"Look into a bt878 card. Works out of the box after one minor tweak to a config file. "

Hi there.  Which minor tweak would that be?  I have a MuchTV Fusion (bt878) with LG PAL-BG + FM tuner and Ubuntu won't recognise it, except as "generic".

I forced it to card=37 tuner=28 and I get video, but just static for sound.

Can you help me?  ;) 

I even have my BtSpy and RegSpy report handy if you need it... 
I have been working on this for hours a day for the past 2 days.  :(  If I can get it working, I'll finally erase my Windows partition.  DScaler was running it just fine in Windows as a generic bt878 (with no MSP).  I have an audio cable that runs from the audio out on the TV tuner card to the line-in on my sound card.

Maybe it would be better just to junk this one and buy one that is supported?  It is the easy way out I suppose, but I'd rather keep trying to make it work.
 
Thanks!

---

### Post by veratyr on 2006-01-03
Well not really a solution to my problem with the asus card but I found my old Wintv card and it has a Fusion 878A chip which works no problem with tvtime. I guess the asus card is going to have to stay in a windows box.

---

