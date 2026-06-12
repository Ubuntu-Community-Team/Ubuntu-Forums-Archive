---
title: "Setting up usb ADSL modem"
date: 2006-07-10
forum: Desktop Environments
---

### Post by xenny on 2006-07-10
Hey there

I've just installed the Dapper Drake version of Ubuntu. I've no previous Linux experience so you'll have to put up with my ignorance I'm afraid ;)

I've tried following the instruction at this link for installing my speedtouch usb modem:
[https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch]("https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch")

But the command 

```
grep -B 1 "THOMSON
ALCATEL" /proc/bus/usb/devices
```

fails. So I've been unable to complete the instructions. 

I've also tried

```
/usr/sbin/lsusb -v
```

which lists nothing.
and with -t which tells me:

"cannot open /proc/bus/usb/devices. No such file or directory"

I tried searching for the modem with 

```
wvdialconf/etc/wvdial.conf
```

I got a response that no modem was detected.

I'm now sort of at a bit of a loss! I'd be really greatful for any advice. I know it would be easier to switch to ethernet but I'd rather not give up so easily. So any suggestions would be welcomed. 

Many thanks

Xenny

---

### Post by melissawm on 2006-07-10
To me they worked fine. What happens if you type

```
sudo dmesg | grep speedtch
```

? Can you post the results here?

---

### Post by xenny on 2006-07-10
Hey, thanks a lot for responding. Ok I've done that. Here's the result:

```
xenny@localhost:~$ sudo dmesg
[4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[4294667.296000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[4294667.296000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[4294667.296000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 511MB LOWMEM available.
[4294667.296000] found SMP MP-table at 000f5ea0
[4294667.296000] On node 0 totalpages: 131056
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 126960 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI 2.2 present.
[4294667.296000] ACPI: RSDP (v000 VT8366                                ) @ 0x000f7860
[4294667.296000] ACPI: RSDT (v001 VT8366 MSI ACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3000
[4294667.296000] ACPI: FADT (v001 VT8366 MSI ACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3040
[4294667.296000] ACPI: MADT (v001 VT8366 MSI ACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff6740
[4294667.296000] ACPI: DSDT (v001 VT8366 MSI ACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x4008
[4294667.296000] ACPI: Local APIC address 0xfee00000
[4294667.296000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[4294667.296000] Processor #0 6:4 APIC version 16
[4294667.296000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[4294667.296000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
[4294667.296000] ACPI: IRQ0 used by override.
[4294667.296000] ACPI: IRQ2 used by override.
[4294667.296000] ACPI: IRQ9 used by override.
[4294667.296000] ACPI: IRQ11 used by override.
[4294667.296000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[4294667.296000] Using ACPI (MADT) for SMP configuration information
[4294667.296000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfff0000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda2 ro quiet splash
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[4294667.296000] Detected 1399.913 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294669.989000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[4294669.992000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294670.019000] Memory: 508852k/524224k available (1976k kernel code, 14796k reserved, 606k data, 288k init, 0k highmem)
[4294670.019000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294670.079000] Calibrating delay using timer specific routine.. 2801.40 BogoMIPS (lpj=1400704)
[4294670.079000] Security Framework v1.0.0 initialized
[4294670.079000] SELinux:  Disabled at boot.
[4294670.079000] Mount-cache hash table entries: 512
[4294670.079000] CPU: After generic identify, caps: 0183fbff c1c7fbff 00000000 00000000 00000000 00000000 00000000
[4294670.079000] CPU: After vendor identify, caps: 0183fbff c1c7fbff 00000000 00000000 00000000 00000000 00000000
[4294670.079000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[4294670.079000] CPU: L2 Cache: 256K (64 bytes/line)
[4294670.079000] CPU: After all inits, caps: 0183fbff c1c7fbff 00000000 00000020 00000000 00000000 00000000
[4294670.079000] mtrr: v2.0 (20020519)
[4294670.079000] CPU: AMD Athlon(tm) Processor stepping 04
[4294670.079000] Enabling fast FPU save and restore... done.
[4294670.079000] Checking 'hlt' instruction... OK.
[4294670.083000] checking if image is initramfs... it is
[4294670.869000] Freeing initrd memory: 6608k freed
[4294670.891000] ACPI: Looking for DSDT ... not found!
[4294670.902000] ENABLING IO-APIC IRQs
[4294670.902000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[4294671.013000] NET: Registered protocol family 16
[4294671.013000] EISA bus registered
[4294671.013000] ACPI: bus type pci registered
[4294671.023000] PCI: PCI BIOS revision 2.10 entry at 0xfb160, last bus=1
[4294671.023000] PCI: Using configuration type 1
[4294671.024000] ACPI: Subsystem revision 20051216
[4294671.033000] ACPI: Interpreter enabled
[4294671.033000] ACPI: Using IOAPIC for interrupt routing
[4294671.034000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294671.034000] PCI: Probing PCI hardware (bus 00)
[4294671.034000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294671.037000] Boot video device is 0000:01:00.0
[4294671.037000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294671.038000] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[4294671.038000] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *9
[4294671.039000] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
[4294671.039000] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
[4294671.043000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294671.043000] pnp: PnP ACPI init
[4294671.047000] pnp: PnP ACPI: found 12 devices
[4294671.047000] PnPBIOS: Disabled by ACPI PNP
[4294671.047000] PCI: Using ACPI for IRQ routing
[4294671.047000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294671.048000] PCI: Bridge: 0000:00:01.0
[4294671.048000]   IO window: disabled.
[4294671.048000]   MEM window: dc000000-ddffffff
[4294671.048000]   PREFETCH window: d0000000-d7ffffff
[4294671.048000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[4294671.049000] audit: initializing netlink socket (disabled)
[4294671.049000] audit(1152567908.048:1): initialized
[4294671.049000] VFS: Disk quotas dquot_6.5.1
[4294671.049000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294671.049000] Initializing Cryptographic API
[4294671.049000] io scheduler noop registered
[4294671.049000] io scheduler anticipatory registered
[4294671.049000] io scheduler deadline registered
[4294671.049000] io scheduler cfq registered
[4294671.049000] isapnp: Scanning for PnP cards...
[4294671.406000] isapnp: No Plug & Play device found
[4294671.422000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294671.424000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294671.424000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294671.424000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294671.424000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294671.425000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294671.427000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294671.427000] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294671.428000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294671.428000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.428000] ide: Assuming 50MHz system bus speed for PIO modes; override with idebus=xx
[4294671.428000] mice: PS/2 mouse device common for all mice
[4294671.428000] EISA: Probing bus 0 at eisa.0
[4294671.428000] Cannot allocate resource for EISA slot 1
[4294671.428000] Cannot allocate resource for EISA slot 4
[4294671.428000] EISA: Detected 0 cards.
[4294671.428000] NET: Registered protocol family 2
[4294671.437000] IP route cache hash table entries: 8192 (order: 3, 32768 bytes)[4294671.437000] TCP established hash table entries: 32768 (order: 5, 131072 bytes)
[4294671.437000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[4294671.438000] TCP: Hash tables configured (established 32768 bind 32768)
[4294671.438000] TCP reno registered
[4294671.438000] TCP bic registered
[4294671.438000] NET: Registered protocol family 1
[4294671.438000] NET: Registered protocol family 8
[4294671.438000] NET: Registered protocol family 20
[4294671.438000] Using IPI Shortcut mode
[4294671.438000] ACPI wakeup devices:
[4294671.438000] SLPB PCI0 USB0 USB1 USB2 MODM UAR1 ECP1
[4294671.438000] ACPI: (supports S0 S1 S4 S5)
[4294671.438000] Freeing unused kernel memory: 288k freed
[4294671.448000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294671.507000] vga16fb: initializing
[4294671.507000] vga16fb: mapped to 0xc00a0000
[4294671.629000] Console: switching to colour frame buffer device 80x25
[4294671.629000] fb0: VGA16 VGA frame buffer device
[4294672.734000] Capability LSM initialized
[4294672.775000] ACPI: Fan [FAN] (on)
[4294672.782000] ACPI: Thermal Zone [THRM] (22 C)
[4294673.528000] Probing IDE interface ide0...
[4294673.914000] hda: ST360020A, ATA DISK drive
[4294674.526000] Probing IDE interface ide1...
[4294675.320000] hdc: LG DVD-ROM DRD-8120B, ATAPI CD/DVD-ROM drive
[4294676.034000] hdd: LG CD-RW CED-8080B, ATAPI CD/DVD-ROM drive
[4294676.034000] Probing IDE interface ide2...
[4294676.547000] Probing IDE interface ide3...
[4294677.060000] Probing IDE interface ide4...
[4294677.573000] Probing IDE interface ide5...
[4294678.086000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294678.086000] ide1 at 0x170-0x177,0x376 on irq 15
[4294678.096000] hda: max request size: 128KiB
[4294678.097000] hda: 117231408 sectors (60022 MB) w/2048KiB Cache, CHS=65535/16/63
[4294678.097000] hda: cache flushes not supported
[4294678.097000]  hda: hda1 hda2 hda3 < hda5 >
[4294678.173000] hdc: ATAPI 40X DVD-ROM drive, 512kB Cache
[4294678.173000] Uniform CD-ROM driver Revision: 3.20
[4294678.182000] hdd: ATAPI 32X CD-ROM CD-R/RW drive, 2048kB Cache
[4294678.694000] Attempting manual resume
[4294678.741000] EXT3-fs: mounted filesystem with ordered data mode.
[4294678.761000] kjournald starting.  Commit interval 5 seconds
[4294705.316000] Real Time Clock Driver v1.12
[4294705.412000] input: PC Speaker as /class/input/input1
[4294705.614000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[4294705.854000] Floppy drive(s): fd0 is 1.44M
[4294705.859000] ts: Compaq touchscreen protocol output
[4294705.901000] parport: PnPBIOS parport detected.
[4294705.901000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[4294705.908000] FDC 0 is a post-1991 82077
[4294707.154000] lp0: using parport0 (interrupt-driven).
[4294707.236000] Adding 1309256k swap on /dev/hda5.  Priority:-1 extents:1 across:1309256k
[4294707.312000] EXT3 FS on hda2, internal journal
[4294707.571000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294707.571000] md: bitmap version 4.39
[4294708.349000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294708.816000] cdrom: open failed.
[4294709.101000] cdrom: open failed.
[4294711.592000] ACPI: Power Button (FF) [PWRF]
[4294711.592000] ACPI: Power Button (CM) [PWRB]
[4294711.592000] ACPI: Sleep Button (CM) [SLPB]
[4294711.763000] ibm_acpi: ec object not found
[4294711.799000] pcc_acpi: loading...
[4294712.488000] powernow: No powernow capabilities detected
[4294720.524000] ppdev: user-space parallel port driver
[4294722.362000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4294722.362000] apm: overridden by ACPI.
[4294728.563000] Bluetooth: Core ver 2.8
[4294728.563000] NET: Registered protocol family 31
[4294728.563000] Bluetooth: HCI device and connection manager initialized
[4294728.563000] Bluetooth: HCI socket layer initialized
[4294728.648000] Bluetooth: L2CAP ver 2.8
[4294728.648000] Bluetooth: L2CAP socket layer initialized
[4294728.666000] Bluetooth: RFCOMM socket layer initialized
[4294728.666000] Bluetooth: RFCOMM TTY layer initialized
[4294728.666000] Bluetooth: RFCOMM ver 1.7
[4294751.965000] NET: Registered protocol family 10
[4294751.965000] lo: Disabled Privacy Extensions
[4294751.966000] IPv6 over IPv4 tunneling driver
[4294761.295000] ISO 9660 Extensions: Microsoft Joliet Level 3
[4294761.467000] ISOFS: changing to secondary root
```

---

### Post by melissawm on 2006-07-10
Actually, i'm not an expert, so what i see is this. If i type that command here i get

```
[17179590.580000] usbcore: registered new driver speedtch
[17179591.760000] speedtch 1-1:1.0: found stage 1 firmware speedtch-1.bin
[17179592.024000] speedtch 1-1:1.0: found stage 2 firmware speedtch-2.bin

```

So, your modem doesn't actually appear there. I can only guess it's either not properly connected/powered or ubuntu doesn't see it for some weird reason... Can't help you any further in the second case. Sorry...

---

### Post by xenny on 2006-07-10
Thanks for your help though. I thought that was probably the case. It's definitely plugged in and working as I'm using it now in Windows! So I guess it's the latter. 

Does anyone know why this would be? And what I might do about it.

---

### Post by melissawm on 2006-07-17
So, just quickly, if you do 

```
sudo /usr/sbin/lsusb -v
```

you get *nothing*? notice the sudo; if i do it without a sudo i get a bunch of stuff but no modem. with sudo, i see in the middle of a lot of stuff i can't actually read, this

```

 idVendor           0x06b9 Alcatel Telecom
  idProduct          0x4061 SpeedTouch ISDN or ADSL Modem
  bcdDevice            4.00
  iManufacturer           1 THOMSON
  iProduct                2 Speed Touch 330
  iSerial                 3 000E506AEE9E
  bNumConfigurations      1

```

are you sure it gives you nothing?

---

### Post by HJD on 2006-07-20
Hi I am in this same boat also a newbe so please help as would love to use this os but it seems to be hard to solve this speebtouch problem also my HP7260 will not work I also I am running live from the CD does this make any diferance,sorry to but in

---

