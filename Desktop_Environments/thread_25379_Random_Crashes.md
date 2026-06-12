---
title: "Random Crashes"
date: 2005-04-10
forum: Desktop Environments
---

### Post by honeywelljr on 2005-04-10
For some reason my system randomly just crashes.  Every now and then it is just the xserver and I am able to Ctrl/Alt/Backspace and restart the xserver.  However, the vast majority of the time I can't do anything.  I can only restart and try again.  Sometime I am up for hours with no problem... more recently I am not able to stay up for more than a few minutes.  I tried searching the issue but the only thing I could think to search for is "random crashes" or "system crash"  niether of wich brought up anything that helped.  Any Ideas where to even start? or better search terms?  Is there somewhere that would store some kind of information that could tell me what is going on?

(I haven't installed anything new, and it crashes usually just after clicking something but the program doesn't seem to matter.  I have been in random games, synaptic, in a terminal, and even in firefox when it crashes)

(on a happy note I love Ubuntu so much <newbie alert> that I just installed it on an ancient laptop to go with my wonderful new desktop OS)

---

### Post by ions on 2005-04-10
Are you using xcompmgr?  It's been pretty stable for me but you never know and I've heard a few horror stories.

Have you done a ram test?  Does dmesg show anything? (Run 'dmesg' at a command prompt).

---

### Post by honeywelljr on 2005-04-10
[QUOTE=ions]Are you using xcompmgr?  It's been pretty stable for me but you never know and I've heard a few horror stories.[/QUOTE]

How would I know if I was using xcompmgr?  I am pretty new to this linux thing.

[QUOTE=ions]
Have you done a ram test?  Does dmesg show anything? (Run 'dmesg' at a command prompt).[/QUOTE]

I am pretty sure ram is fine, wouldn't I get an error when I boot.  I am pretty sure that  it runs a ram test then.  I did the dmesg thing and didn't really find anything other than:
```
[fglrx:firegl_init] *ERROR* Device not found!

```
I know that fglrx has something to do with an ATI card and the "*ERROR*" doesn't sound good.  Nothing else sounded bad, but I really have no Idea what I am looking for.

---

### Post by honeywelljr on 2005-04-10
I did a search on the forums and on the Ubuntu homepage and found several things on xcompmgr... but nothing really saying what it is or how to troubleshoot.  It did, however, look like something that I would have had to have enabled... or loaded... or did something to start using it.  It didn't sound like it was used by default.... I haven't loaded it or enabled it or anything so I would assume this wouldn't be the problem.


What about the error thing I get regarding flgrx?

---

### Post by neighborlee on 2005-04-10
[QUOTE=honeywelljr]I did a search on the forums and on the Ubuntu homepage and found several things on xcompmgr... but nothing really saying what it is or how to troubleshoot.  It did, however, look like something that I would have had to have enabled... or loaded... or did something to start using it.  It didn't sound like it was used by default.... I haven't loaded it or enabled it or anything so I would assume this wouldn't be the problem.


What about the error thing I get regarding flgrx?[/QUOTE]
------------
Hi,

   You could try the 'memtest' item in the initial bootup screen (where you choose ubuntu kernel to start) and let it run quite a while ( hour or so ? im not sure but overnight might be even better to spot random memory corruption: someone else may know for sure)  ..

   I was having similar issues and while I doubt my mem is bad either one never knows.  I was having some odd issues in windows as well but hey who can say if that means anything LOL.

   I wish you luck and if you want to talk realtime I can usuallly be caught in:
irc.freenode.net
#openscenegraph or #neighbors or #heartseed ( our game development channel)

....newbie wize if you've never done IRC...just startup 'xchat' which is under your internet Menu >  choose to see 'edit' options I think it is ( checkbox) >choose 'freenode' from list on left > from there you should be ok ( assuming alot here about your abilities ).

    You can also reach me on 'Gaim' ( internet menu ) under; icq:4684425 or yahoo:imyourhandiman , or even msn : [email]info@heartseed.org[/email] ( I have friends that stoop to this yes ) ..<grin>

cheers
neighborlee

---

### Post by honeywelljr on 2005-04-11
Well it is officially not a memory problem.  I started the Memtest when I left for work at 2:30pm and it is just now after 1:00am and it showed no errors.

What next? :-?

---

### Post by ubuntu_demon on 2005-04-11
[QUOTE=honeywelljr]Well it is officially not a memory problem.  I started the Memtest when I left for work at 2:30pm and it is just now after 1:00am and it showed no errors.

What next? :-?[/QUOTE]
 it is not xcompmgr because you would know if you use it :)

please attach :

~/xsessionerrors
/var/log/Xorg.0.log
dmesg

---

### Post by honeywelljr on 2005-04-11
It won't let me paste the xorg.0.log here, it says it is too long. Is there a specific part that is important? .There is also an xorg.1.log and an xorg.0.log.old.  Are these important?

I am not sure where to go to get "~/xsessionerrors"

But here is "dmesg"

```

Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:12:40 UTC 2005
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 0000000013ff0000 (usable)
 BIOS-e820: 0000000013ff0000 - 0000000013ff8000 (ACPI data)
 BIOS-e820: 0000000013ff8000 - 0000000014000000 (ACPI NVS)
 BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
 BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
 BIOS-e820: 00000000ffee0000 - 00000000fff00000 (reserved)
 BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
319MB LOWMEM available.
On node 0 totalpages: 81904
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 77808 pages, LIFO batch:16
  HighMem zone: 0 pages, LIFO batch:1
DMI 2.3 present.
ACPI: RSDP (v000 AMI                                   ) @ 0x000fa300
ACPI: RSDT (v001 AMIINT SiS735XX 0x00001000 MSFT 0x0100000b) @ 0x13ff0000
ACPI: FADT (v001 AMIINT SiS735XX 0x00001000 MSFT 0x0100000b) @ 0x13ff0030
ACPI: DSDT (v001    SiS      735 0x00000100 MSFT 0x0100000d) @ 0x00000000
ACPI: PM-Timer IO Port: 0x808
Built 1 zonelists
Kernel command line: root=/dev/hdd1 ro quiet splash
Local APIC disabled by BIOS -- you can enable it with "lapic"
mapped APIC to ffffd000 (01285000)
Initializing CPU#0
PID hash table entries: 2048 (order: 11, 32768 bytes)
Detected 995.822 MHz processor.
Using pmtmr for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Memory: 317084k/327616k available (1436k kernel code, 9940k reserved, 754k data, 224k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 1978.36 BogoMIPS (lpj=989184)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000
CPU: After vendor identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000
CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
CPU: L2 Cache: 256K (64 bytes/line)
CPU: After all inits, caps: 0183f9ff c1c7f9ff 00000000 00000020 00000000 00000000
CPU: AMD Athlon(tm) Processor stepping 02
Enabling fast FPU save and restore... done.
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
ACPI: Looking for DSDT in initrd... not found!
ACPI: setting ELCR to 0200 (from 0820)
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4300k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xfdb01, last bus=1
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using PIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
Uncovering SIS18 that hid as a SIS503 (compatible=1)
Enabling SiS 96x SMBus.
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: Power Resource [URP1] (off)
ACPI: Power Resource [URP2] (off)
ACPI: Power Resource [FDDP] (off)
ACPI: Power Resource [LPTP] (off)
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 *11 12 14 15)
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 12 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to bjorn.helgaas@hp.com
** so I can fix the driver.
audit: initializing netlink socket (disabled)
audit(1113197255.509:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
PCI: setting IRQ 11 as level-triggered
ACPI: PCI interrupt 0000:00:02.6[C] -> GSI 11 (level, low) -> IRQ 11
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 2048 buckets, 16Kbytes
TCP: Hash tables configured (established 32768 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices:
PCI0 PS2M PS2K UAR1 UAR2 USB1 USB2  LAN  MDM  AUD SLPB
ACPI: (supports S0 S1 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4300KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
SIS5513: IDE controller at PCI slot 0000:00:02.5
SIS5513: chipset revision 208
SIS5513: not 100% native mode: will probe irqs later
SIS5513: SiS735 ATA 100 (2nd gen) controller
    ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb:DMA
    ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:DMA
Probing IDE interface ide0...
hda: TDK CDRW161040X, ATAPI CD/DVD-ROM drive
hdb: COMPAQ DVD-ROM SD-612B, ATAPI CD/DVD-ROM drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Probing IDE interface ide1...
hdd: QUANTUM FIREBALLlct10 30, ATA DISK drive
ide1 at 0x170-0x177,0x376 on irq 15
hdd: max request size: 128KiB
hdd: 58633344 sectors (30020 MB) w/418KiB Cache, CHS=58168/16/63, UDMA(33)
hdd: cache flushes not supported
 /dev/ide/host0/bus1/target1/lun0: p1 p2 < p5 >
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory... done (458 pages freed)
Restarting tasks... done
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
Adding 931728k swap on /dev/hdd5.  Priority:-1 extents:1
EXT3 FS on hdd1, internal journal
hda: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
hdb: ATAPI 32X DVD-ROM drive, 512kB Cache
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
input: ImExPS/2 Logitech Explorer Mouse on isa0060/serio1
ts: Compaq touchscreen protocol output
fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[fglrx] Maximum main memory to use for locked dma buffers: 257 MBytes.
[fglrx:firegl_init] *ERROR* Device not found!
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: dm-devel@redhat.com
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.10-5-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected SiS 735 chipset
agpgart: Maximum main memory to use for agp memory: 262M
agpgart: AGP aperture is 64M @ 0xd0000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
sis630_smbus 0000:00:02.0: SIS630 comp. bus not detected, module not inserted.
i2c-sis96x version 1.0.0
sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
usbcore: registered new driver usbfs
usbcore: registered new driver hub
ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
PCI: setting IRQ 5 as level-triggered
ACPI: PCI interrupt 0000:00:02.2[D] -> GSI 5 (level, low) -> IRQ 5
ohci_hcd 0000:00:02.2: Silicon Integrated Systems [SiS] USB 1.0 Controller
ohci_hcd 0000:00:02.2: irq 5, pci mem 0xcff5e000
ohci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 3 ports detected
ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
ACPI: PCI interrupt 0000:00:02.3[A] -> GSI 11 (level, low) -> IRQ 11
ohci_hcd 0000:00:02.3: Silicon Integrated Systems [SiS] USB 1.0 Controller (#2)
ohci_hcd 0000:00:02.3: irq 11, pci mem 0xcff5f000
ohci_hcd 0000:00:02.3: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 3 ports detected
sis900.c: v1.08.07 11/02/2003
ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 11
ACPI: PCI interrupt 0000:00:03.0[A] -> GSI 11 (level, low) -> IRQ 11
0000:00:03.0: Realtek RTL8201 PHY transceiver found at address 1.
0000:00:03.0: Using transceiver found at address 1 as default
eth0: SiS 900 PCI Fast Ethernet at 0xcc00, IRQ 11, 00:07:95:b1:b1:a4.
ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
ACPI: PCI interrupt 0000:00:0b.0[A] -> GSI 5 (level, low) -> IRQ 5
NET: Registered protocol family 17
gameport: pci0000:00:0b.1 speed 1217 kHz
Linux video capture interface: v1.00
eth0: Media Link On 100mbps full-duplex
bttv: driver version 0.9.15 loaded
bttv: using 8 buffers with 2080k (520 pages) each for capture
bttv: Bt8xx card found (0).
ACPI: PCI interrupt 0000:00:0f.0[A] -> GSI 5 (level, low) -> IRQ 5
bttv0: Bt878 (rev 17) at 0000:00:0f.0, irq: 5, latency: 64, mmio: 0xcfcfe000
bttv0: detected: ATI TV Wonder/VE [card=64], PCI subsystem ID is 1002:0003
bttv0: using: ATI TV-Wonder VE [card=64,autodetected]
bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
bttv0: using tuner=19
bttv0: i2c: checking for TDA9875 @ 0xb0... not found
bttv0: i2c: checking for TDA7432 @ 0x8a... not found
bttv0: i2c: checking for TDA9887 @ 0x86... not found
tuner: chip found at addr 0xc0 i2c-bus bt878 #0 [sw]
tuner: type set to 19 (Temic PAL* auto (4006 FN5)) by bt878 #0 [sw]
bttv0: registered device video0
bttv0: registered device vbi0
bttv0: PLL: 28636363 => 35468950 .. ok
ACPI: PCI interrupt 0000:00:0f.1[A] -> GSI 5 (level, low) -> IRQ 5
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:11.0[A] -> GSI 5 (level, low) -> IRQ 5
uhci_hcd 0000:00:11.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
uhci_hcd 0000:00:11.0: irq 5, io base 0xbc00
uhci_hcd 0000:00:11.0: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:11.1[B] -> GSI 11 (level, low) -> IRQ 11
uhci_hcd 0000:00:11.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
uhci_hcd 0000:00:11.1: irq 11, io base 0xc000
uhci_hcd 0000:00:11.1: new USB bus registered, assigned bus number 4
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected
usb 4-2: new low speed USB device using uhci_hcd and address 2
ACPI: PCI interrupt 0000:00:11.2[C] -> GSI 5 (level, low) -> IRQ 5
ehci_hcd 0000:00:11.2: VIA Technologies, Inc. USB 2.0
ehci_hcd 0000:00:11.2: irq 5, pci mem 0xcff5ce00
ehci_hcd 0000:00:11.2: new USB bus registered, assigned bus number 5
ehci_hcd 0000:00:11.2: USB 2.0 initialized, EHCI 0.95, driver 26 Oct 2004
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 4 ports detected
usb 4-2: new low speed USB device using uhci_hcd and address 3
usbcore: registered new driver hiddev
usb 4-2: cat timed out on ep0in
drivers/usb/input/hid-core.c: usb_submit_urb(ctrl) failed
drivers/usb/input/hid-core.c: timeout initializing reports

input: USB HID v1.10 Joystick [Logitech Logitech Dual Action] on usb-0000:00:11.1-2
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ACPI: Sleep Button (CM) [SLPB]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
[drm] Initialized drm 1.0.0 20040925
ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 5
ACPI: PCI interrupt 0000:00:09.0[A] -> GSI 5 (level, low) -> IRQ 5
[drm] Initialized radeon 1.14.0 20050125 on minor 0: ATI Technologies Inc Radeon R100 QD [Radeon 7200]
eth0: no IPv6 routers present
ibm_acpi: ec object not found
UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'DVDVolume', timestamp 2004/07/02 13:45 (1ed4)

```

Thank you for helping :grin:

---

### Post by ubuntu_demon on 2005-04-11
~ is your homedir
and it's .xsession-errors (my bad :-P)
so yourhomedir/.xsession-errors

Xorg.0.log is xorgs most recent log file.

And you should attach these files. Attaching is not the same as copy pasting the contents ;)

---

### Post by stoneguy on 2005-04-11
I had that kind of problem - see 
[http://ubuntuforums.org/showthread.php?t=25653](http://ubuntuforums.org/showthread.php?t=25653) 
Your output shows ACPI loading OK, but try turning it off anyway.

---

### Post by honeywelljr on 2005-04-11
Thank you, I hadn't even noticed the attatchment option down at the bottom of the screen.  :oops: 

Here is the xsession-errors and xorg.0.log.


[edit]
okay, I did the upload thing, but I don't see attatchements when I view the message... did I miss something?

[editx2]
I am an idiot.  I just realized that I was uploading in wrong format.  will upload when I get home. (I don't know why I didn't see the error message the first time)

---

### Post by honeywelljr on 2005-04-13
It won't let me attatch the files either... it says they are to big (even one at a time).  now what?

---

### Post by ubuntu_demon on 2005-04-13
[QUOTE=honeywelljr]It won't let me attatch the files either... it says they are to big (even one at a time).  now what?[/QUOTE]
compress them
for example :
$tar cvf -  filenames | gzip > file.tar.gz

---

### Post by philcolbourn on 2005-04-13
I had system freezes where nothing moved, not even a mouse. I put up with it. The hardware was ok under XP. I recently make the pc freeze twice in a row by scp'ing a file from a mac to the pc. This was my first hint that it may have something to do with my network card.
I was using an netgear wg111v2 under ndiswrapper. I pulled it out, installed an old 802.11b zyair b-220 using the driver on sourceforge. I think i also installed fxload to make it work, but that may be my imagination. I have not had a cra

---

### Post by honeywelljr on 2005-04-14
I haven't had alot of time to work on the issue... but I think it is fixed  \\:D/ 

I switched out the monitors.  Just because I got a new one, not because I thought it was the problem.  It hasn't crashed yet, and it has been since my last post.

Why would the monitor cause this kind of problem?

---

### Post by ubuntu_demon on 2005-04-15
[QUOTE=honeywelljr]I haven't had alot of time to work on the issue... but I think it is fixed  \\:D/ 

I switched out the monitors.  Just because I got a new one, not because I thought it was the problem.  It hasn't crashed yet, and it has been since my last post.

Why would the monitor cause this kind of problem?[/QUOTE]
 strange

some other thinks you could check for :
1) heat/cooling maybe your videocard or memory gets overheated .. if it's really a big crash it could be your cpu overheats
2) memory problems somewhere (could be cpu cache,RAM, videomemory). You should test your memory during boot.
3) dust in your pc (not likely most of the people have booting problems instead of freezing problems)

---

### Post by jorgepeixoto on 2005-04-16
Memory probelm doesn´t seem to be the case, he's already run memtest86. 

And I have had a simillar problem to his. Random crashes. I have solved it by underclocking my system: I went to the setup and underclocked the fsb from 133 MHz to 128 MHz. Now it is rock stable, and I really don't care that it is 3.75% slower. 

I have heard that in some cases, forcing your agp card to work with agp 1x (in the xorg.conf file) may correct the problem, but I tried the underclock first and it worked, so I'm done with it. 

So
1-) Try underclocking your computer. First underclock it a lot (say, 30%) and, if the problem gets soved, you have spotted the cause, then you can start increasing the clock at small increments to see the maximum you can get without instabilities. In my system, it was 128 MHz. (before you ask, 128 MHz is the FSB, that is , the external clock. The internal clock of your computer (e.g. 2.1 GHz in my computer) is the FSB x multiplier).  You just have to find the fsb (or external clock, I don´t know what your motherboard manufacturer calls it) and decrease. It is safe, but be aware that the speed of your computer will get slower (what could be dangerous is increasing the fsb beyond the default value, which is called overcloking).If it does not work:
2-) Make shure it is not overheating. If it does not work:
3-) Try forcing your agp card to work with agp 1x.

[]'s

---

### Post by honeywelljr on 2005-04-16
Actually, I switched out monitors and it hasn't done it since. 

I think the monitor was going to sleep and refusing to come back on unless I restarted the xserver or somethimes only after a restart.  That is the only thing I can think of that would allow a monitor change to stop system crashing. :confused:

---

### Post by jorgepeixoto on 2005-04-16
Good that the problem is solved.

But maybe it is a setup thing. From what I recall, there is a setup setting of what your computer should do when waking up your monitor, and if you choose it to something not supported by your video card or monitor, you can have problems. I think it is under the power management menu or something. So, if you switch back to the old monitor, have a look at your setup. 

[]'s

---

### Post by pmjdebruijn on 2005-08-15
Hi,

I also noticed that you are loading ATi's fglrx driver, simultaneously with linux DRI module...

That doesn't sound like a good idea anyway...

Regards,
Pascal de Bruijn

---

### Post by tmasboa on 2005-08-15
I have the same problem, with an ATI Radeon 9250

---

