---
title: "i have come to a conclusion"
date: 2006-05-18
forum: Desktop Environments
---

### Post by runefreak on 2006-05-18
my conclusion is that compaq should be blown up and ess tech staff should be put
in a concentration camp.or somthing equally as horrible i contacted compaq/hp
about my sound problem they were worthless they said that they did not and never would support linux as an os yet they sell linux servers???? go figure 
 so as i was on the phone with a socalled hp support tech i proceeded to tell them what i thought of them. and contacted esstech.com lol what a waste
 this is what i got the most unprofessional response possible from a companies tech support i have ever seen and i quote"
If you are experiencing difficulties with using your sound card and/or
modem, please contact the original manufacturer or marketer of the sound
card and/or modem directly for the assistance. ESS is a chip set
company, not cards / system manufacture. We do not supply end-user
support services to the general public. Rather, ESS works with the OEM
manufacturers to ensure that they have the required software solutions
for their respective products. "unquote .i have also come to the conclusion that
i don`t have to worry about the garbage es1869 sound chip set not working 
as i have a sledge hammer to take care of my problem this chipset was seemingly never invented or put into this pos presario of mine as there is no documentation of it ever being put in a presario 5020 and there is absolutly 
no frigging drivers for it or no means of making it work on linux i have gone through two monitors today and three telephones which i smashed both
if anyone could please help me i would greatly appreciate it.

---

### Post by Resurrection on 2006-05-18
Umm, so what kind of specific issues are you having?  I'm sure you'll get better support from here, if anyone knows the answer.

---

### Post by runefreak on 2006-05-18
ubuntu does not detect the es1869 chipset nor does alsa or lspci or isapnptools](*,) ](*,)

---

### Post by runefreak on 2006-05-18
here is the lspci out put 
0000:00:00.0 Host bridge: Intel Corporation 440LX/EX - 82443LX/EX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 440LX/EX - 82443LX/EX AGP bridge (rev 03)
0000:00:03.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:00:14.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:14.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:14.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:14.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc)

---

### Post by runefreak on 2006-05-18
dmesg output
0000:00:00.0 Host bridge: Intel Corporation 440LX/EX - 82443LX/EX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 440LX/EX - 82443LX/EX AGP bridge (rev 03)
0000:00:03.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:00:14.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:14.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:14.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:14.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc)
mark@R5N5Q6:~$ dmesg
[4294667.296000] Linux version 2.6.15-22-386 (buildd@vernadsky) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Sun May 7 15:49:09 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[4294667.296000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000000c000000 (usable)
[4294667.296000]  BIOS-e820: 00000000fffe0000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 192MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 49152
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 45056 pages, LIFO batch:15
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI not present.
[4294667.296000] ACPI: Unable to locate RSDP
[4294667.296000] Allocating PCI resources starting at 10000000 (gap: 0c000000:f3fe0000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda2 ro quiet splash
[4294667.296000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[4294667.296000] mapped APIC to ffffd000 (01181000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[    0.000000] Detected 300.719 MHz processor.
[   33.216001] Using tsc for high-res timesource
[   33.217600] Console: colour VGA+ 80x25
[   33.219064] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   33.220822] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   33.264409] Memory: 184372k/196608k available (1975k kernel code, 11640k reserved, 607k data, 288k init, 0k highmem)
[   33.264434] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   33.324183] Calibrating delay using timer specific routine.. 602.08 BogoMIPS (lpj=301040)
[   33.324399] Security Framework v1.0.0 initialized
[   33.324455] SELinux:  Disabled at boot.
[   33.324558] Mount-cache hash table entries: 512
[   33.325288] CPU: After generic identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   33.325345] CPU: After vendor identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   33.325396] CPU: L1 I cache: 16K, L1 D cache: 16K
[   33.325416] CPU: After all inits, caps: 0183f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   33.325522] mtrr: v2.0 (20020519)
[   33.325552] CPU: Intel Celeron (Covington) stepping 00
[   33.325577] Enabling fast FPU save and restore... done.
[   33.325599] Checking 'hlt' instruction... OK.
[   33.330083] checking if image is initramfs... it is
[   39.285134] Freeing initrd memory: 6607k freed
[   39.329476] NET: Registered protocol family 16
[   39.329692] EISA bus registered
[   39.344463] PCI: PCI BIOS revision 2.10 entry at 0xfa104, last bus=1
[   39.344504] PCI: Using configuration type 1
[   39.347171] ACPI: Subsystem revision 20051216
[   39.347193] ACPI: Interpreter disabled.
[   39.347266] Linux Plug and Play Support v0.97 (c) Adam Belay
[   39.347339] pnp: PnP ACPI: disabled
[   39.347359] PnPBIOS: Scanning system for PnP BIOS support...
[   39.347494] PnPBIOS: Found PnP BIOS installation structure at 0xc00f5a10
[   39.347520] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x233b, dseg 0xf0000[   39.362657] PnPBIOS: 17 nodes reported by PnP BIOS; 17 recorded by driver
[   39.362780] PCI: Probing PCI hardware
[   39.362803] PCI: Probing PCI hardware (bus 00)
[   39.364005] PCI quirk: region ee00-ee3f claimed by PIIX4 ACPI
[   39.364035] PCI quirk: region ee80-ee8f claimed by PIIX4 SMB
[   39.364695] Boot video device is 0000:01:00.0
[   39.369107] PCI: Using IRQ router PIIX/ICH [8086/7110] at 0000:00:14.0
[   39.399490] PCI: Bridge: 0000:00:01.0
[   39.399523]   IO window: 1000-1fff
[   39.399547]   MEM window: 40000000-410fffff
[   39.399567]   PREFETCH window: 10000000-100fffff
[   39.406798] audit: initializing netlink socket (disabled)
[   39.406873] audit(1147910770.139:1): initialized
[   39.407913] VFS: Disk quotas dquot_6.5.1
[   39.408092] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   39.408573] Initializing Cryptographic API
[   39.408614] io scheduler noop registered
[   39.408674] io scheduler anticipatory registered
[   39.408703] io scheduler deadline registered
[   39.408774] io scheduler cfq registered
[   39.408799] Limiting direct PCI/PCI transfers.
[   39.410628] isapnp: Scanning for PnP cards...
[   39.768301] isapnp: No Plug & Play device found
[   40.056913] PNP: PS/2 Controller [PNP0303,PNP0f0e] at 0x60,0x64 irq 1,12
[   40.060029] serio: i8042 AUX port at 0x60,0x64 irq 12
[   40.060648] serio: i8042 KBD port at 0x60,0x64 irq 1
[   40.061231] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[   40.061909] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   40.092949] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   40.101843] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   40.102497] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   40.102528] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   40.103797] mice: PS/2 mouse device common for all mice
[   40.105524] EISA: Probing bus 0 at eisa.0
[   40.105567] Cannot allocate resource for EISA slot 1
[   40.105583] Cannot allocate resource for EISA slot 2
[   40.105647] EISA: Detected 0 cards.
[   40.105905] NET: Registered protocol family 2
[   40.114318] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   40.115403] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[   40.115722] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[   40.116104] TCP: Hash tables configured (established 8192 bind 8192)
[   40.116122] TCP reno registered
[   40.116678] TCP bic registered
[   40.116754] NET: Registered protocol family 1
[   40.116800] NET: Registered protocol family 8
[   40.116814] NET: Registered protocol family 20
[   40.116937] Using IPI Shortcut mode
[   40.117200] Freeing unused kernel memory: 288k freed
[   40.135431] input: AT Translated Set 2 keyboard as /class/input/input0
[   40.605899] vga16fb: initializing
[   40.605935] vga16fb: mapped to 0xc00a0000
[   40.737190] Console: switching to colour frame buffer device 80x25
[   40.737238] fb0: VGA16 VGA frame buffer device
[   42.017777] Capability LSM initialized
[   46.664509] PIIX4: IDE controller at PCI slot 0000:00:14.1
[   46.664573] PIIX4: chipset revision 1
[   46.664589] PIIX4: not 100% native mode: will probe irqs later
[   46.664627]     ide0: BM-DMA at 0x2020-0x2027, BIOS settings: hda:DMA, hdb:pio
[   46.664696]     ide1: BM-DMA at 0x2028-0x202f, BIOS settings: hdc:DMA, hdd:pio
[   46.664742] Probing IDE interface ide0...
[   46.942884] hda: QUANTUM Bigfoot TX8.0AT, ATA DISK drive
[   47.555066] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   47.556271] Probing IDE interface ide1...
[   48.227472] hdc: LITE-ON LTR-52246S, ATAPI CD/DVD-ROM drive
[   48.535155] ide1 at 0x170-0x177,0x376 on irq 15
[   48.638844] hda: max request size: 128KiB
[   48.638877] hda: 15698592 sectors (8037 MB) w/69KiB Cache, CHS=15574/16/63, UDMA(33)
[   48.638910] hda: cache flushes not supported
[   48.640363]  hda: hda1 hda2 hda3 < hda5 >
[   48.737350] hdc: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   48.737406] Uniform CD-ROM driver Revision: 3.20
[   49.925887] usbcore: registered new driver usbfs
[   49.928286] usbcore: registered new driver hub
[   49.952151] USB Universal Host Controller Interface driver v2.3
[   49.954674] PCI: Found IRQ 11 for device 0000:00:14.2
[   49.954811] uhci_hcd 0000:00:14.2: UHCI Host Controller
[   49.957262] uhci_hcd 0000:00:14.2: new USB bus registered, assigned bus number 1
[   49.957322] uhci_hcd 0000:00:14.2: irq 11, io base 0x00002000
[   49.959950] hub 1-0:1.0: USB hub found
[   49.960056] hub 1-0:1.0: 2 ports detected
[   50.457922] Attempting manual resume
[   50.650449] EXT3-fs: mounted filesystem with ordered data mode.
[   50.745676] kjournald starting.  Commit interval 5 seconds
[   97.374106] Linux agpgart interface v0.101 (c) Dave Jones
[   97.419384] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   97.482992] Linux Tulip driver version 1.1.13 (December 15, 2004)
[   97.483592] PCI: Found IRQ 11 for device 0000:00:03.0
[   97.484191] tulip0:  MII transceiver #1 config 1000 status 786d advertising 05e1.
[   97.490933] eth0: ADMtek Comet rev 17 at 00012400, 00:03:6D:1C:5E:9D, IRQ 11.[   97.533926] agpgart: Detected an Intel 440LX Chipset.
[   97.542941] agpgart: AGP aperture is 64M @ 0x50000000
[   97.589657] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   98.117963] piix4_smbus 0000:00:14.3: Found 0000:00:14.3 device
[   98.118063] piix4_smbus 0000:00:14.3: Host SMBus controller not enabled!
[   98.704678] input: PS/2 Generic Mouse as /class/input/input1
[   99.524103] parport: PnPBIOS parport detected.
[   99.524187] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   99.966604] Floppy drive(s): fd0 is 1.44M
[   99.979673] FDC 0 is a post-1991 82077
[  101.892181] Real Time Clock Driver v1.12
[  102.140784] input: PC Speaker as /class/input/input2
[  103.262904] ts: Compaq touchscreen protocol output
[  106.432814] NET: Registered protocol family 17
[  107.166479] Intel ISA PCIC probe: not found.
[  107.589162] lp0: using parport0 (interrupt-driven).
[  108.209669] 0000:00:03.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972117)
[  108.209727] eth0: Setting full-duplex based on MII#1 link partner capability of 41e1.
[  108.253304] Adding 188960k swap on /dev/hda5.  Priority:-1 extents:1 across:188960k
[  108.496940] EXT3 FS on hda2, internal journal
[  109.821359] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[  109.821386] md: bitmap version 4.39
[  110.605120] NET: Registered protocol family 10
[  110.605910] lo: Disabled Privacy Extensions
[  110.607157] IPv6 over IPv4 tunneling driver
[  112.469520] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[  113.977986] cdrom: open failed.
[  121.033573] eth0: no IPv6 routers present
[  139.679211] ppdev: user-space parallel port driver
[  149.842007] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  153.048776] Bluetooth: Core ver 2.8
[  153.048814] NET: Registered protocol family 31
[  153.048827] Bluetooth: HCI device and connection manager initialized
[  153.048897] Bluetooth: HCI socket layer initialized
[  153.192758] Bluetooth: L2CAP ver 2.8
[  153.192793] Bluetooth: L2CAP socket layer initialized
[  153.509975] Bluetooth: RFCOMM socket layer initialized
[  153.510059] Bluetooth: RFCOMM TTY layer initialized
[  153.510075] Bluetooth: RFCOMM ver 1.7
[  155.154339] hdc: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[  155.154432] hdc: drive_cmd: error=0x04 { AbortedCommand }
[  155.154452] ide: failed opcode was: 0xec

---

### Post by Resurrection on 2006-05-18
Well, this is all I have gathered so far:

[ALSA site listing for ESS chips / cards]("http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-ESS_Technology#matrix")

[Instructions from ALSA site for ESS 18xx]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=ESS+Technology&card=.&chip=ES18xx&module=es18xx")

I'm not sure if that helps you or not, but worth a look.

Edit:  On second thought, these seem to be for Plug and Play ESS 1869 card, not the onboard chipset.....same with the OSS site:
[http://www.opensound.com/osshw.html]("http://www.opensound.com/osshw.html")

Not sure if those do you any good or not.

---

### Post by runefreak on 2006-05-18
cat /proc/version output
Linux version 2.6.15-22-386 (buildd@vernadsky) (gcc version 4.0.3 (Ubuntu 4.0.3- 1ubuntu5)) #1 PREEMPT Sun May 7 15:49:09 UTC 2006

---

### Post by runefreak on 2006-05-18
thanks but no it did not work would not let me install the driver

---

### Post by MonkeyBoy on 2006-05-18
I had problems with es1869 on an Armada 3500 but managed to get my soundcard detected using the advice on this link:

[http://ubuntuforums.org/showthread.php?t=66865&highlight=es18xx](http://ubuntuforums.org/showthread.php?t=66865&highlight=es18xx)

You are right about Compaq though.  They don't seem very helpful at all.

---

### Post by everett3rd on 2006-05-18
runefreak;

"my conclusion is that compaq should be blown up and ess tech staff should be put in a concentration camp." A bit extreme don't you think?

I have been dealing with HP/Compaq (Sepreatly and now togther) for over 20 years and I have never had a support call that moved me to destroy a phone.

I don't know of any major PC maker that supports Linux on their **Consumer** product line. Only a few support it on their Server hardware.

Also Server hardware support is very different from Consumer hardware support (and it costs much more too, expertise is **not** cheap.). 
**ALL** PC makers only support what they sell. Compaq sold you a Presario with Windows on it and they will support Winodws on that hardware. Why would they pay people to support it with Linux if they don't sell it with Linux?

As far as ESS goes...
They told you the truth. They make chips, not sound cards. How can you expect them to support something they did not make? It would be like calling Champion spark plugs and asking them why your car won't start since you replaced the ignition control system. They know nothing past the ends of the spark plug.

Perhaps you can solve this issue the way I solved my Wireless networking problems. My Linksys card would not work well with Linux (after 2 weeks of messing with it), I went and bought a Netgear card that did.

If you can't find a good answer here (where there are Linux experts):
Disable the unsupported hardware in your BIOS setup and get a sound card that does work with Linux. Sound cards can be found for less than $30.00 or so. Surley this is FAR less than the cost of the time and frustration you have spent so far.

-Everett

---

### Post by runefreak on 2006-05-18
lol the reason i destroyed my phone was that as soon as i said i installed linux on my pc the tech became very rude .and i would love to disable the chipset in my bios only there is no option to do so or disable anything else for that matter
and i do have a linux compatible soundcard which i payed 30 dollars for it`s a soundblaster audigy but i can`t install it because the es chipset will not disable therefor i can not install a new soundcard because it also is not recognized by windows or linux due to that stupid little isa sound set

---

