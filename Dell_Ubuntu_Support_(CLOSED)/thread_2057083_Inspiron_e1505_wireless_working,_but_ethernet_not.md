---
title: "Inspiron e1505 wireless working, but ethernet not"
date: 2012-09-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by beanud on 2012-09-12
Hello, I just got gifted an Inspiron e1505 and installed Ubuntu 12.04 on it and it runs great. Just two problems, the wireless and ethernet don't work. I followed the instructions [here]("http://askubuntu.com/questions/38327/how-can-i-get-broadcom-bcm4311-wireless-working/38700#38700") and [here]("http://ubuntuforums.org/showthread.php?t=2002044&highlight=bcm4401-b0&page=2")[]("http://ubuntuforums.org/showthread.php?t=2002044&highlight=bcm4401-b0&page=2") and manged to finally get the wireless working. Unfortunately, my provider only does wired connections, so I'm still stuck.

Can anyone help me out? I've been a casual linux user for years, but some times I fail at doing really complicated things.

Here's the output of lspci

> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

ifconfig

> eth1      Link encap:Ethernet  HWaddr 00:15:c5:12:94:ed  
          inet6 addr: fe80::215:c5ff:fe12:94ed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1971 errors:0 dropped:0 overruns:0 frame:0
          TX packets:125 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:213290 (213.2 KB)  TX bytes:28287 (28.2 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:352 errors:0 dropped:0 overruns:0 frame:0
          TX packets:352 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28576 (28.5 KB)  TX bytes:28576 (28.5 KB)

lsmod

> Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
uas                    17699  0 
usb_storage            39646  1 
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
arc4                   12473  2 
dell_laptop            13671  0 
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
rfcomm                 38139  0 
b43                   342643  0 
bnep                   17830  2 
parport_pc             32114  0 
dcdbas                 14098  1 dell_laptop
bluetooth             158438  10 rfcomm,bnep
ppdev                  12849  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
binfmt_misc            17292  1 
mac80211              436455  1 b43
r852                   17901  0 
sm_common              16737  1 r852
nand                   49667  2 r852,sm_common
nand_ids                8547  1 nand
r592                   17808  0 
psmouse                72846  0 
joydev                 17393  0 
mtd                    35584  2 sm_common,nand
snd_seq_midi_event     14475  1 snd_seq_midi
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
serio_raw              13027  0 
memstick               15857  1 r592
nand_ecc               13070  1 nand
i915                  414603  3 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
cfg80211              178679  2 b43,mac80211
bcma                   25651  1 b43
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13077  0 
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
b44                    31364  0 
firewire_ohci          40172  0 
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
ssb                    50691  2 b43,b44

rfkill list all
> 
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

Please help, this computer is miles ahead of what I'm using now and I'd love to be able to use it.

[]("http://askubuntu.com/questions/38327/how-can-i-get-broadcom-bcm4311-wireless-working/38700#38700")

---

### Post by beanud on 2012-09-13
Ok, by the looks of ifconfig, it looks like the computer is sending packets, but the connection won't establish. I did dmesg and got this, which is longer than my buffer allows, but here's what I got.

dmesg
> 
[    0.243514] pci_bus 0000:0b: resource 1 [mem 0xdfd00000-0xdfdfffff]
[    0.243518] pci_bus 0000:0b: resource 2 [mem 0x40000000-0x401fffff 64bit pref]
[    0.243522] pci_bus 0000:0c: resource 0 [io  0xd000-0xdfff]
[    0.243525] pci_bus 0000:0c: resource 1 [mem 0xdfa00000-0xdfcfffff]
[    0.243529] pci_bus 0000:0c: resource 2 [mem 0xd0000000-0xd01fffff 64bit pref]
[    0.243533] pci_bus 0000:03: resource 1 [mem 0xdf900000-0xdf9fffff]
[    0.243537] pci_bus 0000:03: resource 4 [io  0x0000-0xffff]
[    0.243540] pci_bus 0000:03: resource 5 [mem 0x00000000-0xffffffff]
[    0.243594] NET: Registered protocol family 2
[    0.243693] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.244032] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.244789] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.245165] TCP: Hash tables configured (established 131072 bind 65536)
[    0.245168] TCP reno registered
[    0.245173] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.245186] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.245301] NET: Registered protocol family 1
[    0.245325] pci 0000:00:02.0: Boot video device
[    0.245365] pci 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.245392] pci 0000:00:1d.0: PCI INT A disabled
[    0.245407] pci 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.245431] pci 0000:00:1d.1: PCI INT B disabled
[    0.245447] pci 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.245470] pci 0000:00:1d.2: PCI INT C disabled
[    0.245485] pci 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.245509] pci 0000:00:1d.3: PCI INT D disabled
[    0.245521] pci 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.245553] pci 0000:00:1d.7: PCI INT A disabled
[    0.245591] PCI: CLS 64 bytes, default 64
[    0.245667] Simple Boot Flag at 0x79 set to 0x1
[    0.246078] audit: initializing netlink socket (disabled)
[    0.246092] type=2000 audit(1347536937.240:1): initialized
[    0.276681] Trying to unpack rootfs image as initramfs...
[    0.315018] highmem bounce pool size: 64 pages
[    0.315027] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.332219] VFS: Disk quotas dquot_6.5.2
[    0.332327] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.333185] fuse init (API version 7.17)
[    0.333338] msgmni has been set to 1710
[    0.348506] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.348550] io scheduler noop registered
[    0.348553] io scheduler deadline registered
[    0.348564] io scheduler cfq registered (default)
[    0.348745] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.348815] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.348915] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.348975] pcieport 0000:00:1c.3: irq 41 for MSI/MSI-X
[    0.349107] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.349145] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.349250] intel_idle: MWAIT substates: 0x22220
[    0.349252] intel_idle: does not run on family 6 model 14
[    0.372102] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.372602] ACPI: AC Adapter [AC] (on-line)
[    0.373513] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.373939] ACPI: Lid Switch [LID]
[    0.374007] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.374014] ACPI: Power Button [PBTN]
[    0.374084] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.374089] ACPI: Sleep Button [SBTN]
[    0.374261] Marking TSC unstable due to TSC halts in idle
[    0.374276] ACPI: acpi_idle registered with cpuidle
[    0.379370] thermal LNXTHERM:00: registered as thermal_zone0
[    0.379374] ACPI: Thermal Zone [THM] (32 C)
[    0.379398] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.379412] ACPI: Battery Slot [BAT0] (battery present)
[    0.392088] ERST: Table is not found!
[    0.392092] GHES: HEST is not enabled!
[    0.392264] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.396496] isapnp: Scanning for PnP cards...
[    0.402780] Linux agpgart interface v0.103
[    0.402893] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[    0.402955] agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable
[    0.403338] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.403487] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    0.456662] brd: module loaded
[    0.457826] loop: module loaded
[    0.458092] ata_piix 0000:00:1f.2: version 2.13
[    0.458125] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.458133] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.458182] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.468253] scsi0 : ata_piix
[    0.468374] scsi1 : ata_piix
[    0.476268] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    0.476273] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    0.476877] Fixed MDIO Bus: probed
[    0.476913] tun: Universal TUN/TAP device driver, 1.6
[    0.476916] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.477012] PPP generic driver version 2.4.2
[    0.477158] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.477187] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.477211] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.477216] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.477271] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.477297] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.477311] ehci_hcd 0000:00:1d.7: debug port 1
[    0.481194] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.488574] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xffa80000
[    0.504384] ACPI: Battery Slot [BAT0] (battery present)
[    0.512204] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.512457] hub 1-0:1.0: USB hub found
[    0.512464] hub 1-0:1.0: 8 ports detected
[    0.512599] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.512627] uhci_hcd: USB Universal Host Controller Interface driver
[    0.512666] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.512681] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.512686] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.512746] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.512781] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bf80
[    0.512967] hub 2-0:1.0: USB hub found
[    0.512973] hub 2-0:1.0: 2 ports detected
[    0.513069] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.513079] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.513084] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.513141] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.513189] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000bf60
[    0.513367] hub 3-0:1.0: USB hub found
[    0.513372] hub 3-0:1.0: 2 ports detected
[    0.513467] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.513477] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.513481] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.513541] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.513586] uhci_hcd 0000:00:1d.2: irq 22, io base 0x0000bf40
[    0.513764] hub 4-0:1.0: USB hub found
[    0.513770] hub 4-0:1.0: 2 ports detected
[    0.513864] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.513874] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.513879] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.513932] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.513976] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000bf20
[    0.514159] hub 5-0:1.0: USB hub found
[    0.514165] hub 5-0:1.0: 2 ports detected
[    0.514332] usbcore: registered new interface driver libusual
[    0.514404] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.520652] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.520663] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.520851] mousedev: PS/2 mouse device common for all mice
[    0.521081] rtc_cmos 00:06: RTC can wake from S4
[    0.521249] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.521285] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.521384] device-mapper: uevent: version 1.0.3
[    0.521483] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email]
[    0.521538] EISA: Probing bus 0 at eisa.0
[    0.521548] Cannot allocate resource for EISA slot 1
[    0.521552] Cannot allocate resource for EISA slot 2
[    0.521581] EISA: Detected 0 cards.
[    0.521595] cpufreq-nforce2: No nForce2 chipset.
[    0.521646] cpuidle: using governor ladder
[    0.521721] cpuidle: using governor menu
[    0.521724] EFI Variables Facility v0.08 2004-May-17
[    0.522109] TCP cubic registered
[    0.522294] NET: Registered protocol family 10
[    0.523097] NET: Registered protocol family 17
[    0.524695] Registering the dns_resolver key type
[    0.524724] Using IPI No-Shortcut mode
[    0.525958] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.526155] PM: Hibernation image not present or could not be loaded.
[    0.526172] registered taskstats version 1
[    0.676569] ata2.00: ATAPI: PHILIPS DVD+/-RW SDVD8820, AD15, max UDMA/33
[    0.733005] ata2.00: configured for UDMA/33
[    0.788658] ata1.00: HPA detected: current 75200265, native 78140160
[    0.788667] ata1.00: ATA-7: Hitachi HTS541040G9SA00, MB2OC60G, max UDMA/100
[    0.788671] ata1.00: 75200265 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    0.824771] ata1.00: configured for UDMA/100
[    0.987894] isapnp: No Plug & Play device found
[    1.008218] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54104 MB2O PQ: 0 ANSI: 5
[    1.008485] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.008755] sd 0:0:0:0: [sda] 75200265 512-byte logical blocks: (38.5 GB/35.8 GiB)
[    1.008828] sd 0:0:0:0: [sda] Write Protect is off
[    1.008832] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.008864] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.009936] scsi 1:0:0:0: CD-ROM            PHILIPS  DVD+-RW SDVD8820 AD15 PQ: 0 ANSI: 5
[    1.018662] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.018667] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.018842] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.019034] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.081095]  sda: sda1 sda2 < sda5 >
[    1.081613] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.136361] usb 5-1: new low-speed USB device number 2 using uhci_hcd
[    1.151716] Freeing initrd memory: 13796k freed
[    1.167602]   Magic number: 12:946:832
[    1.167751] rtc_cmos 00:06: setting system clock to 2012-09-13 11:48:58 UTC (1347536938)
[    1.168214] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.168218] EDD information not available.
[    1.168426] Freeing unused kernel memory: 740k freed
[    1.168818] Write protecting the kernel text: 5828k
[    1.168838] Write protecting the kernel read-only data: 2376k
[    1.168841] NX-protecting the kernel data: 4412k
[    1.190308] udevd[85]: starting version 175
[    1.377312] b43-pci-bridge 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.377327] b43-pci-bridge 0000:0b:00.0: setting latency timer to 64
[    1.405102] sdhci: Secure Digital Host Controller Interface driver
[    1.405107] sdhci: Copyright(c) Pierre Ossman
[    1.405472] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 19)
[    1.405504] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.406552] mmc0: no vmmc regulator found
[    1.407583] Registered led device: mmc0::
[    1.408723] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[    1.408734] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[    1.408745] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[    1.408755] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[    1.425297] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[    1.425335] firewire_ohci 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.472800] ssb: Sonics Silicon Backplane found on PCI device 0000:0b:00.0
[    1.489832] firewire_ohci: Added fw-ohci device 0000:03:01.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x11
[    1.496169] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.516062] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[    1.516075] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[    1.516086] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[    1.530693] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/input/input4
[    1.548978] generic-usb 0003:1BCF:0007.0001: input,hiddev0,hidraw0: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:1d.3-1/input0
[    1.549002] usbcore: registered new interface driver usbhid
[    1.549005] usbhid: USB HID core driver
[    1.568169] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    1.568217] b44: Broadcom 44xx/47xx 10/100 PCI ethernet driver version 2.0
[    1.589011] b44 ssb1:0: eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver 00:15:c5:12:94:ed
[    1.791900] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    1.988204] firewire_core: created device fw0: GUID 474fc0003cb4f121, S400
[   18.101637] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.157189] udevd[307]: starting version 175
[   18.250320] lp: driver loaded but no devices found
[   18.270025] Adding 1036284k swap on /dev/sda5.  Priority:-1 extents:1 across:1036284k 
[   18.353439] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input5
[   18.353554] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   18.353584] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   18.526741] [drm] Initialized drm 1.1.0 20060810
[   18.548835] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   18.582820] cfg80211: Calling CRDA to update world regulatory domain
[   18.603385] intel_rng: FWH not detected
[   18.623775] leds_ss4200: no LED devices found
[   18.724296] r592 0000:03:01.2: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   18.724308] r592 0000:03:01.2: setting latency timer to 64
[   18.732932] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.732940] i915 0000:00:02.0: setting latency timer to 64
[   18.733148] r592: driver successfully loaded
[   18.745786] r852 0000:03:01.3: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   18.745797] r852 0000:03:01.3: setting latency timer to 64
[   18.748054] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   18.748057] [drm] Driver supports precise vblank timestamp query.
[   18.750604] r852: Non dma capable device detected, dma disabled
[   18.750624] r852: driver loaded successfully
[   18.809208] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   18.946264] udevd[344]: renamed network interface eth0 to eth1
[   19.024842] type=1400 audit(1347536956.353:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=541 comm="apparmor_parser"
[   19.025476] type=1400 audit(1347536956.353:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=541 comm="apparmor_parser"
[   19.025848] type=1400 audit(1347536956.353:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=541 comm="apparmor_parser"
[   19.227617] Bluetooth: Core ver 2.16
[   19.227648] NET: Registered protocol family 31
[   19.227651] Bluetooth: HCI device and connection manager initialized
[   19.227655] Bluetooth: HCI socket layer initialized
[   19.227657] Bluetooth: L2CAP socket layer initialized
[   19.227664] Bluetooth: SCO socket layer initialized
[   19.232140] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   19.242449] ppdev: user-space parallel port driver
[   19.285367] type=1400 audit(1347536956.613:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=581 comm="apparmor_parser"
[   19.305559] type=1400 audit(1347536956.633:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=581 comm="apparmor_parser"
[   19.328855] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.328860] Bluetooth: BNEP filters: protocol multicast
[   19.335976] Bluetooth: RFCOMM TTY layer initialized
[   19.335984] Bluetooth: RFCOMM socket layer initialized
[   19.335986] Bluetooth: RFCOMM ver 1.11
[   19.383011] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   19.466126] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   19.466132] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.466135] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   19.466140] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.466143] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   19.466147] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.466151] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   19.466155] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.466158] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   19.466162] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.466165] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   19.466169] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.466173] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   19.466177] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.466180] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   19.466184] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.466188] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   19.466192] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.466195] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   19.466199] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.466203] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   19.466207] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.466210] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   19.466214] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   19.466218] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   19.466222] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   19.466225] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   19.466229] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   19.470591] psmouse serio1: synaptics: Touchpad model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000/0x0
[   19.506470] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   19.606098] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   19.615396] init: failsafe main process (610) killed by TERM signal
[   19.641388] Registered led device: b43-phy0::tx
[   19.641456] Registered led device: b43-phy0::rx
[   19.641524] Registered led device: b43-phy0::radio
[   19.641576] Broadcom 43xx driver loaded [ Features: PNL ]
[   19.695845] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.703498] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   19.705440] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   19.790273] type=1400 audit(1347536957.117:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=703 comm="apparmor_parser"
[   19.801632] type=1400 audit(1347536957.129:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=705 comm="apparmor_parser"
[   19.806795] type=1400 audit(1347536957.133:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=705 comm="apparmor_parser"
[   19.807170] type=1400 audit(1347536957.133:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=705 comm="apparmor_parser"
[   19.866511] type=1400 audit(1347536957.193:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=708 comm="apparmor_parser"
[   19.913035] [drm] initialized overlay support
[   20.111219] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   20.111225] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.111229] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   20.111233] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.111237] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   20.111241] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.111244] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   20.111248] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.111252] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   20.111256] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.111259] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   20.111263] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.111267] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   20.111271] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.111274] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   20.111278] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.111281] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   20.111286] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.111289] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   20.111293] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.111296] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   20.111300] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.111304] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   20.111308] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.111311] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   20.111315] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.111319] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   20.111323] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.111328] cfg80211: World regulatory domain updated:
[   20.111330] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   20.111334] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.111338] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.111342] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.111346] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.111349] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.333385] fbcon: inteldrmfb (fb0) is primary device
[   20.336876] Console: switching to colour frame buffer device 160x50
[   20.336925] fb0: inteldrmfb frame buffer device
[   20.336928] drm: registered panic notifier
[   20.336990] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   20.337043] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   20.337123] snd_hda_intel 0000:00:1b.0: irq 42 for MSI/MSI-X
[   20.337160] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   20.351550] init: alsa-restore main process (793) terminated with status 19
[   20.512962] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   20.513256] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   49.457022] audit_printk_skb: 36 callbacks suppressed
[   49.457028] type=1400 audit(1347536986.785:24): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=2164 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[   53.816207] b44 ssb1:0: eth1: Link is up at 100 Mbps, full duplex
[   53.816213] b44 ssb1:0: eth1: Flow control is off for TX and off for RX
[   53.816509] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   58.892059] usb 1-5: new high-speed USB device number 3 using ehci_hcd
[   59.131690] Initializing USB Mass Storage driver...
[   59.138695] scsi2 : usb-storage 1-5:1.0
[   59.138824] usbcore: registered new interface driver usb-storage
[   59.138827] USB Mass Storage support registered.
[   59.181257] usbcore: registered new interface driver uas
[   60.213473] scsi 2:0:0:0: Direct-Access     Kingston DataTraveler 108 PMAP PQ: 0 ANSI: 0 CCS
[   60.216504] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   61.432192] sd 2:0:0:0: [sdb] 15240576 512-byte logical blocks: (7.80 GB/7.26 GiB)
[   61.432678] sd 2:0:0:0: [sdb] Write Protect is off
[   61.432683] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[   61.433184] sd 2:0:0:0: [sdb] No Caching mode page present
[   61.433191] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   61.437688] sd 2:0:0:0: [sdb] No Caching mode page present
[   61.437697] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   61.458237]  sdb: sdb1
[   61.462670] sd 2:0:0:0: [sdb] No Caching mode page present
[   61.462676] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   61.462680] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   64.616019] eth1: no IPv6 routers present
[  112.176019] eth1: no IPv6 routers present
[  160.648053] eth1: no IPv6 routers present
[  209.616042] eth1: no IPv6 routers present
[  257.288040] eth1: no IPv6 routers present
[  305.344054] eth1: no IPv6 routers present

I tried ignoring IPPv6 in network connections, but got nothing.

---

### Post by zbomb on 2012-09-20
i have been using an inspiron e1505 for years
and have installed ubuntu on it from 9.10 up to 12.04
wireless cards and connections in general were a pain in the ***.
haha
did you install all the drivers for hardware?

---

### Post by beanud on 2012-09-20
haha, yeah, that's the feeling I'm getting. I installed all the drivers I could find. including the nonfree versions. That's what got my wireless to work. Maybe I'm missing some? I'm pretty sure I have b44, which I think is the recommended one for this computer.

---

