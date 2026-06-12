---
title: "Help with D-Link AirPlus DWL-650+ card config"
date: 2005-10-17
forum: Desktop Environments
---

### Post by Adam Boettiger on 2005-10-17
Hello -

I'm still working on getting wireless access on my G4 Mac PowerBook laptop that is dual-partitioned with Linux Ubuntu and Mac OS X. 

The card I am trying to configure is:

D-Link AirPlus DWL-650+ 2.4GHz Wireless Cardbus Adapter. I've quoted and provided some of the relevant information you requested and included it below. Any help in getting this to work would be greatly appreciated! Thanks in advance.

Adam Boettiger


PREFACE

Interestingly, while a couple of weeks ago I previously could not get the card to work at all, last night I downloaded the final release of 5.10 and did a clean install and it appeared to find/"see" the card on install just fine and work out of the box with no adjustments at all. Last night was surfing via the card. Then it started to exhibit behavior that I can only describe as turning itself (the card) on and off. In other words, works once at bootup, then stops. So I'm close!

Kudos to the developers for the release!

I'm very close to getting the card to work.


1. If this is a question about getting a component PCI device working; soundcards, network cards, wireless network cards, video cards, etc... paste in the output of

/sbin/lspci

<output>
adam@ubuntu:/sbin$ lspci
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 AGP
0000:00:10.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 PCI
0001:10:12.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
0001:10:13.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
0001:10:17.0 ff00: Apple Computer Inc. KeyLargo/Intrepid Mac I/O
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:1a.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:1b.0 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.1 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
0001:11:00.0 Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface
0002:24:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 Internal PCI
0002:24:0d.0 ff00: Apple Computer Inc. UniNorth/Intrepid ATA/100
0002:24:0e.0 FireWire (IEEE 1394): Apple Computer Inc. UniNorth 2 FireWire (rev 81)
0002:24:0f.0 ffff: Apple Computer Inc. UniNorth 2 GMAC (Sun GEM) (rev ff)
adam@ubuntu:/sbin$

</output>

2. Next up, what kernel AND distro are you using, the VIA 8233 sound card worked in 2.4.16, then disappeared until 2.4.20. This is of course unless you are using Mandrake or SuSe who had working ALSA modules. When in doubt of the kernel:

uname -r

<output>
Kernel: 2.6.12-9-powerpc
Distro: Linux Ubuntu, 5.10 PPC
</output>

3. If the problem stems from a laptop pcmcia card, similar info to /sbin/lspci can be found from:

/sbin/cardctl ident

<output>
adam@ubuntu:/sbin$ cardctl ident
Socket 0:
  no product info available
adam@ubuntu:/sbin$

</output>

That is of course unless its a Cardbus card, they're pretty easy to tell apart, it'll be marked on the card, it'll probably be a big selling point on the packing, the manual, etc. too. Cardbus cards appear under /sbin/lspci, pretty neat eh?

5. When in doubt, drop in some logs. For instance, the command: "dmesg", is literally, the kernel ring buffer, its a record of everything the kernel saw as it loaded, in order.

<output>
adam@ubuntu:/sbin$ dmesg
r USB Mass Storage devices
[   90.932231] usb-storage: device found at 3
[   90.932235] usb-storage: waiting for device to settle before scanning
[   90.932248] usbcore: registered new driver usb-storage
[   90.932252] USB Mass Storage support registered.
[   90.951314] usbcore: registered new driver hiddev
[   90.961208] input: USB HID v1.10 Mouse [Logitech USB Trackball] on usb-0001:10:1b.0-1.3
[   90.961220] usbcore: registered new driver usbhid
[   90.961224] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[   91.551020] Attempting manual resume
[   91.551232] swsusp: Suspend partition has wrong signature?
[   91.580891] EXT3-fs: INFO: recovery required on readonly filesystem.
[   91.580900] EXT3-fs: write access will be enabled during recovery.
[   94.059380] kjournald starting.  Commit interval 5 seconds
[   94.059411] EXT3-fs: hda3: orphan cleanup on readonly fs
[   94.059423] ext3_orphan_cleanup: deleting unreferenced inode 1277085
[   94.059497] ext3_orphan_cleanup: deleting unreferenced inode 2257470
[   94.059508] EXT3-fs: hda3: 2 orphan inodes deleted
[   94.059512] EXT3-fs: recovery complete.
[   94.085251] EXT3-fs: mounted filesystem with ordered data mode.
[   95.119231] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   95.938137]   Vendor: I0MEGA    Model: Mini512MB*IOM2A3  Rev: 4.70
[   95.938154]   Type:   Direct-Access                      ANSI SCSI revision: 00
[   95.946892] usb-storage: device scan complete
[   96.218137] SCSI device sda: 1019392 512-byte hdwr sectors (522 MB)
[   96.225108] sda: Write Protect is off
[   96.225112] sda: Mode Sense: 45 00 00 08
[   96.225115] sda: assuming drive cache: write through
[   96.244119] SCSI device sda: 1019392 512-byte hdwr sectors (522 MB)
[   96.251108] sda: Write Protect is off
[   96.251112] sda: Mode Sense: 45 00 00 08
[   96.251115] sda: assuming drive cache: write through
[   96.251127]  /dev/scsi/host0/bus0/target0/lun0: p1
[   96.265168] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0[   99.020909] Adding 857412k swap on /dev/hda6.  Priority:-1 extents:1
[   99.265855] EXT3 FS on hda3, internal journal
[  104.233442] apm_emu: APM Emulation 0.5 initialized.
[  104.619654] ieee1394: Initialized config rom entry `ip1394'
[  104.634791] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[  105.670905] adt746x: version 1 (supported)
[  105.670916] adt746x: Thermostat bus: 1, address: 0x2e, limit_adjust: 0, fan_speed: -1
[  105.670922] sensor 0: CPU/INTREPID BOTTOMSIDE
[  105.670926] sensor 1: CPU BOTTOMSIDE
[  105.670929] sensor 2: PWR SUPPLY BOTTOMSIDE
[  105.687336] adt746x: ADT7460 initializing
[  105.702602] adt746x: Lowering max temperatures from 73, 73, 73 to 70, 50, 70
[  105.709839] adt746x: Setting speed to 0 for CPU BOTTOMSIDE fan.
[  105.839383] adt746x: Setting speed to 0 for PWR SUPPLY BOTTOMSIDE fan.
[  109.635353] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[  110.468001] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[  110.468012] hdc: packet command error: error=0x50 { LastFailedSense=0x05 }
[  110.468018] ide: failed opcode was: unknown
[  110.468745] cdrom: open failed.
[  112.325136] adt746x: setting fans speed to 64 (limit exceeded by 0 on CPU BOTTOMSIDE)
[  112.325146] adt746x: Setting speed to 64 for CPU BOTTOMSIDE fan.
[  112.326190] adt746x: Setting speed to 64 for PWR SUPPLY BOTTOMSIDE fan.
[  112.602019] Linux agpgart interface v0.101 (c) Dave Jones
[  112.618044] agpgart: Detected Apple UniNorth 2 chipset
[  112.618143] agpgart: configuring for size idx: 4
[  112.647298] agpgart: AGP aperture is 16M @ 0x0
[  112.956773] Linux Kernel Card Services
[  112.956783]   options:  [pci] [cardbus] [pm]
[  112.982101] Yenta: CardBus bridge found at 0001:10:13.0 [0000:0000]
[  112.982141] Yenta: Enabling burst memory read transactions
[  112.982147] Yenta: Using CSCINT to route CSC interrupts to PCI
[  112.982150] Yenta: Routing CardBus interrupts to PCI
[  112.982156] Yenta TI: socket 0001:10:13.0, mfunc 0x00001002, devctl 0x60
[  113.082889] Yenta: ISA IRQ mask 0x0000, PCI irq 53
[  113.082895] Socket status: 30000868
[  114.049264] acx100: It looks like you've been coaxed into buying a wireless network card
[  114.049273] acx100: that uses the mysterious ACX100/ACX111 chip from Texas Instruments.
[  114.049276] acx100: You should better have bought e.g. a PRISM(R) chipset based card,
[  114.049279] acx100: since that would mean REAL vendor Linux support.
[  114.049282] acx100: Given this info, it's evident that this driver is still EXPERIMENTAL,
[  114.049285] acx100: thus your mileage may vary. Reading README file and/or Craig's HOWTO is
[  114.049289] recommended, visit [http://acx100.sf.net](http://acx100.sf.net) in case of further questions/discussion.
[  114.049299] acx100: Warning: compiled to use 16bit I/O access only (compatibility mode). Set Makefile ACX_IO_WIDTH=32 to use slightly problematic 32bit mode
[  114.049305] Running on a BIG-ENDIAN CPU
[  114.049308] acx_init_module: dev_info is: TI acx_pci
[  114.049312] acx_init_module: TI acx_pci.o: Ver 0.2.0pre8 driver initialized, waiting for cards to probe...
[  114.056793] PCI: Enabling device 0001:11:00.0 (0000 -> 0003)
[  114.056834] Found ACX100-based wireless network card at 0001:11:00.0, irq:53, phymem1:0xf3010000, phymem2:0xf3000000, mem1:0xf2584000, mem1_size:4096, mem2:0xf2680000, mem2_size:65536
[  114.056841] initial debug setting is 0x001b
[  114.056871] acx_select_io_register_set: using ACX100 io resource addresses (size: 56)
[  114.056875] hw_unavailable = 1
[  114.056881] acx_probe_pci: TI acx_pci: Using IRQ 53
[  114.056904] reset hw_unavailable++
[  114.056910] acx_reset_mac: enable soft reset...
[  114.056915] acx_reset_mac: disable soft reset and go to init mode...
[  114.068956] Requesting firmware image 'WLANGEN.BIN'
[  114.201127] not using auto increment for firmware loading
[  114.272835] acx_write_fw: firmware written
[  114.342282] acx_write_fw (firmware): 0, acx_validate_fw: 0
[  114.351854] acx_reset_dev: boot up eCPU and wait for complete...
[  114.551851] acx_reset_dev: Received signal that card is ready to be configured :) (the eCPU has woken up)
[  114.570435] reset hw_unavailable--
[  114.570451] acx100: allocated net device wlan0, driver compiled against wireless extensions v17 and Linux 2.6.12-9-powerpc
[  114.570863] ******************************************
[  114.570866] ************* acx_init_mac_1 *************
[  114.570869] ******************************************
[  114.570873] ==> Get the mailbox pointers from the scratch pad registers
[  114.570881] CmdMailboxOffset = fdc8
[  114.570883] InfoMailboxOffset = ff4c
[  114.570885] <== Get the mailbox pointers from the scratch pad registers
[  114.570890] CommandParameters = [ 0xf268fdcc ]
[  114.570892] InfoParameters = [ 0xf268ff50 ]
[  114.570995] Requesting firmware image 'RADIO0d.BIN'
[  114.712096] not using auto increment for firmware loading
[  114.712859] acx_write_fw: firmware written
[  114.713564] acx_write_fw (radio): 0, acx_validate_fw: 0
[  114.852817] CodeEnd:50A20000
[  114.852908] acx100_init_wep: writing WEP options.
[  114.856138] get_mask 0x00004d82, set_mask 0x00000000
[  114.856209] Got sensitivity value 176
[  114.856273] Got antenna value 0x8D
[  114.856336] Got Energy Detect (ED) threshold 112
[  114.856399] Got Channel Clear Assessment (CCA) value 13
[  114.856459] Got regulatory domain 0x10
[  114.856464] get_mask 0x00000000, set_mask 0x00000000 - after update
[  114.856877] new ratevector: 82 84 0b 16 2c
[  114.856884] setting RXconfig to 2000:0000
[  114.856948] Beacon length:59
[  114.857109] hw_unavailable--
[  114.857187] acx100: form factor 0x01 ((mini-)PCI / CardBus), radio type 0x0d (Maxim), EEPROM version 0x05. Uploaded firmware 'Rev 1.9.8.b' (0x01030505).
[  114.859009] creating /proc entry driver/acx_wlan0
[  114.859025] creating /proc entry driver/acx_wlan0_diag
[  114.859029] creating /proc entry driver/acx_wlan0_eeprom
[  114.859034] creating /proc entry driver/acx_wlan0_phy
[  114.859039] acx_probe_pci: TI acx_pci.o: Ver 0.2.0pre8 loaded successfully
[  114.869330] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[  114.869363] PCI: Enabling device 0002:24:0e.0 (0000 -> 0002)
[  114.872595] ohci1394: fw-host0: Unexpected PCI resource length of 1000!
[  114.924925] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[40]  MMIO=[f5000000-f50007ff]  Max Packet=[4096]
[  116.196285] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000a95fffe9732d8]
[  116.341556] Bluetooth: Core ver 2.7
[  116.341570] NET: Registered protocol family 31
[  116.341573] Bluetooth: HCI device and connection manager initialized
[  116.341591] Bluetooth: HCI socket layer initialized
[  116.345109] Bluetooth: HCI USB driver ver 2.8
[  116.349351] usbcore: registered new driver hci_usb
[  117.569851] ts: Compaq touchscreen protocol output
[  118.556399] module count ++
[  118.556406] OPENING DEVICE
[  118.556417] acx_set_status: Setting status = 1 (SCANNING)
[  118.556431] <acx_set_timer> Elapse = 2500000
[  118.556435] attempt to set the timer when the card interface is not up!
[  118.556439] ACX100 f/w ver >= 1.9.3.e or ACX111 --> using s/w timer
[  118.556443] initial settings update on iface activation.
[  118.556448] get_mask 0x00000000, set_mask 0x0037eefc
[  118.556451] important setting has been changed --> need to update packet templates, too
[  118.556466] Updating Tx fallback to 0 retries
[  118.556534] Updating transmit power: 18 dBm
[  118.556538] changing radio power level to 18 dBm (23)
[  118.556548] Updating antenna value: 0x8D
[  118.556613] Updating Energy Detect (ED) threshold: 112
[  118.556684] Updating Channel Clear Assessment (CCA) value: 0x0D
[  118.556747] Updating channel: 1
[  118.556749] Updating: enable Tx
[  118.566826] Updating: enable Rx on channel: 1
[  118.576824] Updating short retry limit: 7, long retry limit: 4
[  118.576951] Updating Tx MSDU lifetime: 4096
[  118.577013] Updating regulatory domain: 0x10
[  118.577078] setting RXconfig to 2010:0fdd
[  118.577147] Updating WEP key settings
[  118.577151] Setting WEP key 0 as default.
[  118.577273] Starting radio scan
[  118.586823] acx_set_status: Setting status = 1 (SCANNING)
[  118.586828] <acx_set_timer> Elapse = 2500000
[  118.586831] attempt to set the timer when the card interface is not up!
[  118.586835] get_mask 0x00000000, set_mask 0x00000000 - after update
[  118.586840] FIXME: most likely needs refinement, first implementation version only...
[  118.586859] FIXME: most likely needs refinement, first implementation version only...
[  118.587236] FIXME: most likely needs refinement, first implementation version only...
[  118.587249] get_mask 0x00000000, set_mask 0x00000040
[  118.587254] setting RXconfig to 2010:0fdd
[  118.587323] get_mask 0x00000000, set_mask 0x00000000 - after update
[  118.587336] FIXME: most likely needs refinement, first implementation version only...
[  118.587342] get_mask 0x00000000, set_mask 0x00000040
[  118.587346] setting RXconfig to 2010:0fdd
[  118.587411] get_mask 0x00000000, set_mask 0x00000000 - after update
[  118.607350] NET: Registered protocol family 17
[  119.694358] <acx_sta_list_add> sta=00:14:bf:76:74:4d
[  119.694373] found and registered station: ESSID "" on channel 6, BSSID 00:14:bf:76:74:4d, Access Point, caps 0x0001, SIR 34, SNR 0
[  119.796765] found and registered station: ESSID "" on channel 6, BSSID 00:14:bf:76:74:4d, Access Point, caps 0x0001, SIR 41, SNR 0
[  120.669455] <acx_sta_list_add> sta=00:09:5b:9e:49:58
[  120.669469] found and registered station: ESSID "NETGEAR" on channel 11, BSSID 00:09:5b:9e:49:58, Access Point, caps 0x0005, SIR 18, SNR 3
[  120.705515] <acx_sta_list_add> sta=00:0f:b5:27:42:9e
[  120.705521] found and registered station: ESSID "Ponderosa" on channel 11, BSSID 00:0f:b5:27:42:9e, Access Point, caps 0x0021, SIR 24, SNR 3
[  120.771838] found and registered station: ESSID "NETGEAR" on channel 11, BSSID 00:09:5b:9e:49:58, Access Point, caps 0x0005, SIR 22, SNR 3
[  120.807914] found and registered station: ESSID "Ponderosa" on channel 11, BSSID 00:0f:b5:27:42:9e, Access Point, caps 0x0021, SIR 27, SNR 3
[  120.832632] Got Info IRQ: status 0x8000, type 0x0001: scan complete
[  120.832644] <Scan Table>: SSID="",CH=6,SIR=41,SNR=0
[  120.832648] peer_cap 0x0001, needed_cap 0x0001
[  120.832652] found station with empty or single-space (hidden) SSID, considering for assoc attempt
[  120.832657] <Scan Table>: SSID="NETGEAR",CH=11,SIR=22,SNR=3
[  120.832660] peer_cap 0x0005, needed_cap 0x0001
[  120.832664] ESSID doesn't match! ("NETGEAR" station, "Hephaestus" config)
[  120.832668] <Scan Table>: SSID="Ponderosa",CH=11,SIR=27,SNR=3
[  120.832671] peer_cap 0x0021, needed_cap 0x0001
[  120.832675] ESSID doesn't match! ("Ponderosa" station, "Hephaestus" config)
[  120.832683] acx_complete_dot11_scan: matching station found: 00:14:bf:76:74:4d, joining
[  120.832690] acx_cmd_join_bssid rates_basic 0003->03, rates_supported 0127->1f[  120.842801] <acx_cmd_join_bssid> BSS_Type = 2
[  120.842806] <acx_cmd_join_bssid> JoinBSSID MAC:00:14:bf:76:74:4d
[  120.842810] Sending authentication1 request, awaiting response!
[  120.842827] acx_set_status: Setting status = 2 (WAIT_AUTH)
[  120.842841] <acx_set_timer> Elapse = 1500000
[  120.847741] 00:0d:88:89:fe:0a 00:0d:88:89:fe:0a 00:14:bf:76:74:4d 00:14:bf:76:74:4d 00:14:bf:76:74:4d
[  120.847753] Algorithm is ok
[  120.847755] acx_process_authen auth seq step 2
[  120.847759] acx_set_status: Setting status = 3 (AUTHENTICATED)
[  120.847763] <acx_set_timer> Elapse = 1500000
[  120.847767] Sending association request, awaiting response! NOT ASSOCIATED YET.
[  120.847774] association: requesting caps 0x0100, ESSID Hephaestus
[  120.850296] acx_set_status: Setting status = 4 (ASSOCIATED)
[  120.850305] ASSOCIATED!
[  122.346772] acx_timer: status = 4
[  123.357862] FIXME: most likely needs refinement, first implementation version only...
[  123.357883] get_mask 0x00000000, set_mask 0x00000040
[  123.357890] setting RXconfig to 2010:0fdd
[  123.357961] get_mask 0x00000000, set_mask 0x00000000 - after update
[  123.357984] FIXME: most likely needs refinement, first implementation version only...
[  123.357990] get_mask 0x00000000, set_mask 0x00000040
[  123.357993] setting RXconfig to 2010:0fdd
[  123.358055] get_mask 0x00000000, set_mask 0x00000000 - after update
[  124.812713] NET: Registered protocol family 10
[  124.812891] Disabled Privacy Extensions on device c026ad58(lo)
[  124.813007] FIXME: most likely needs refinement, first implementation version only...
[  124.813065] FIXME: most likely needs refinement, first implementation version only...
[  124.813110] IPv6 over IPv4 tunneling driver
[  124.813163] get_mask 0x00000000, set_mask 0x00000040
[  124.813171] setting RXconfig to 2010:0fdd
[  124.813249] get_mask 0x00000000, set_mask 0x00000000 - after update
[  125.429971] wlan0: duplicate address detected!
[  138.824339] Bluetooth: L2CAP ver 2.7
[  138.824349] Bluetooth: L2CAP socket layer initialized
[  138.877649] Bluetooth: RFCOMM ver 1.5
[  138.877666] Bluetooth: RFCOMM socket layer initialized
[  138.877682] Bluetooth: RFCOMM TTY layer initialized
[  154.374473] adt746x: Stopping fans.
[  154.374495] adt746x: Setting speed to 0 for CPU BOTTOMSIDE fan.
[  154.376145] adt746x: Setting speed to 0 for PWR SUPPLY BOTTOMSIDE fan.
[  164.097973] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[  609.696361] cs: memory probe 0x80000000-0x80ffffff: excluding 0x80000000-0x80ffffff
adam@ubuntu:/sbin$

</output>

Other good ones, bits of /var/log/messages

Couldn't get an output.


IWCONFIG OUTPUT

adam@ubuntu:/$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+  ESSID:"Hephaestus"  Nickname:"acx100 v0.2.0pre8"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:BF:76:74:4D
          Bit Rate=22 Mb/s   Tx-Power=18 dBm   Sensitivity=176/255
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality=52/100  Signal level=34/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

adam@ubuntu:/$



IFCONFIG OUTPUT

adam@ubuntu:/$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3529 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3529 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:320549 (313.0 KiB)  TX bytes:320549 (313.0 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0D:88:89:FE:0A
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:88ff:fe89:fe0a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:30402 (29.6 KiB)  TX bytes:1511 (1.4 KiB)
          Interrupt:53 Base address:0x1000

adam@ubuntu:/$


Thank you.

Adam Boettiger
Portland, Oregon

---

### Post by darius_underhill on 2005-10-17
Hi! This Thread might help

[HOWTO: Using D-link AirplusG+ DWL g650+ with ndiswrapper]("http://www.ubuntuforums.org/showthread.php?t=74651")

---

### Post by SickTwist on 2005-10-18
Adam,
First of all, thank you for providing such thorough information with your question. You've set a nice example. I would also like to add that I am by no means a wireless expert but I'm going to try my best to help you figure this out. :)

From the output of lspci, I can see that your card is using the TI ACX 100 chipset. The chipset is the most important part of any piece of hardware when trying to determine what driver to use and how well the hardware will work in Linux. As darius_underhill has suggested, you could try to use your card's Windows driver in Linux by using ndiswrapper. There is another option, though: [The ACX100/ACX111 wireless network driver project]("http://acx100.sourceforge.net/") is working to create a native Linux driver for your card. (Their website hosts a [wiki]("http://acx100.sourceforge.net/mediawiki/"), [mailing lists]("http://sourceforge.net/mailarchive/forum.php?forum_id=31812"), and a [forum]("http://sourceforge.net/forum/forum.php?forum_id=257272")--all of which might be better equipped to handle this particular problem than the Ubuntu forums). 

Looking at the output of dmesg reveals that the driver, acx_pci is already installed and detects your card at boot. However, appears to give an error message that your card's [ESSID]("http://en.wikipedia.org/wiki/ESSID") does not match NETGEAR and Ponderosa. You should probably look into correcting that first.

Best of luck!

---

### Post by Copter on 2006-02-21
hi!

im using the same card but with a PC laptop. according to your iwconfig everything looks fine for me. i had lots of strange issues with this card but after all it works quite well. here are my tricks. maybe it can help you :)

everytime i run kde i have to manualy run this script
```

#! /bin/sh

ifdown wlan0

sleep 1

iwconfig wlan0 essid "myname"
iwconfig wlan0 channel 1
iwconfig wlan0 mode Managed
iwconfig wlan0 ap 00:31:02:AA:BB:CC
iwconfig wlan0 rate auto
iwconfig wlan0 key s:1234-5678-9ABC-DEF0-1234-5678-9A
iwconfig wlan0 key open
iwconfig wlan0 txpower 18
#16/190
#18/170
#18/190 ?
iwconfig wlan0 sens 190
#60 ok
#190 +/-
#170 ok++!
iwconfig wlan0 power off
iwconfig wlan0 commit

sleep 1

ifup wlan0

route add default gw 192.168.0.1 dev wlan0
```the tricky things are **sens** and **txpower**. values i wrote there were found by using some random combinations (txpower 16-18, sens 20-250). for example it works great on 18/170 but doesnt on 18/150 and below and 18/190 and above. i havent got idea why.

on these magic-number-combinations i still get rx and tx errors in logs but i dont care much unless it recieves signal. using _bad_ number combinations causes that this card is unable to find _any_ network around.

hope it helps. btw. on my computer this card worked out-of-the-box (except these stupid number lottery). did not have to install any drivers nor manualy configure ndiswrapper.

good luck!

copter :]

---

