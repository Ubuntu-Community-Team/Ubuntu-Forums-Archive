---
title: "Problema amb capturadora de TV i webcam"
date: 2008-01-17
forum: Catalan Team
---

### Post by klonner on 2008-01-17
Bones 

he tornat a instal·lar ubuntu com a sistema principal al meu ordinador després de molt temps i tinc un problema que abans no tenia, la webcam l'amsn no em deixa configurar-la dona error, i que si vull enviar la informació o ignorar l'error....

després la capturadora no hi ha cap programa que em funcioni, un en comptes de la capturadora m'agafa la imatge de la webcam i si li intento anar a preferències i canviar, llavors es penja i es tanca...

el meu pc es: AMD64 3500+, placa ASUS A8V, gràfica ATI 9550, 1Gb Ram, la capturadora es una AverMedia te bastants anys ja, i no havia tingut cap problema l'anterior vegada, la webcam posa Airis escrit, la regalaven a la Caixa Catalunya fa un temps amb el carnet universitari.

Tinc la distribució Ubuntu 7.10 de 32Bits

Gracies

---

### Post by pespin on 2008-01-17
Prova a córrer el programa que dius que se't penja des de la terminal, a veure si deixa algun rastre que ens pugui ser útil.

D'altra banda, pots concretar l'error del amsn?

fes "ls -l /dev/video*" i enganxa'n el resultat :)

---

### Post by papapep on 2008-01-17
Un

```
lsusb
```

i 

```
lspci
```

per veure quins xips porten aquests dispositius anirien bé.

Enganxa el resultat aquí, si us plau.

---

### Post by klonner on 2008-01-18
l'error del l'amsn es produeix durant l'execució de l'asistent per configurar la webcam, diu "

"s'ha produit un error de TK, problablement perque hi ha un error a l'amsn. Si us plau informa'ns fent click al botó informar. fes click per veure els detalls, pem ok per continuar xatejant amb l'amsn"

els detalls que dona apretant a detalls es:


can't read "brightness": no such variable
    while executing
"::Capture::SetBrightness $grabber $brightness"
    (procedure "setPic" line 31)
    invoked from within
"setPic $::CAMGUI::webcam_preview"
    (procedure "::AVAssistant::StartPreviewLinux" line 52)
    invoked from within
"::AVAssistant::StartPreviewLinux .assistant1.bodyf.contentf.left.chans Television"
    ("after" script)


mirant els dispositus usb....

lsusb
Bus 004 Device 002: ID 0c45:600d Microdia 
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 0ace:1211 ZyDAS 802.11b/g USB2 WiFi
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c040 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000


mirant els dispositus PCI....

lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
00:0e.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
00:0e.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)



Codi que deixa el XavTV

$ xawtv
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.22-14-generic)
xinerama 0: 1024x768+0+0
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  69
  Current serial number in output stream:  69

Directament no fa res.....

$ zapping

** (zapping:10511): WARNING **: GConf key '/apps/zapping/plugins/deinterlace/method' is unset and has no default. Schemas incomplete or not installed?

(C) 2000-2004 Iñaki G. Etxebarria, Michael H. Schimek.
This program is freely redistributable under the terms
of the GNU General Public License.

Using video device '/dev/video0', display ':0.0', screen 0.
Querying frame buffer parameters from X server.
DMA not possible on screen 0.
Setup failed. Try -vv for details.

(zapping:10511): Gtk-CRITICAL **: gtk_list_store_get_value: assertion `VALID_ITER (iter, list_store)' failed

(zapping:10511): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.14.1/gobject/gtype.c:3339: type id `0' is invalid

(zapping:10511): GLib-GObject-WARNING **: can't peek value table for type `<invalid>' which is not currently referenced
Segmentation fault (core dumped)

Aquest em carrega la webcam, i si intento anar a preferencies, es penja.....


$ tvtime
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/klonner/.tvtime/tvtime.xml
Thank you for using tvtime.


Aquest em surt la pantalla blava i no signal....


Gracies a tots per la vostra ajuda!

---

### Post by klonner on 2008-01-21
helppppp meeeee  :(


amb un live cd (koppix) la tv va perfectament

---

### Post by papapep on 2008-01-21
> 00:0e.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)

Segons això, en teoria un:

```
modprobe bt878
```

hauria de fer que et funcioni la placa.

---

### Post by klonner on 2008-01-25
vaig escriure aixo a la consola però cap programa funcionava...

ara tinc suse i amb suse funciona bé, me la reconeix com Avermedia TV 98, però suse es molt molt lent per carregar!

---

### Post by papapep on 2008-01-25
Però et va mostrar algun missatge?? Et va arribar a carregar el mòdul??

Fes a un terminal:

```
lsmod |grep bt
```

després fes:

```
modprobe bt878
```

i torna a fer:

```
lsmod |grep bt
```

i enganxa el resultat de cada ordre.

Per cert, també ajudaria que enganxessis el resultat d'executar un

```
lsmod
```

a la Suse.

---

### Post by patrickfromspain on 2008-01-25
proba el kdetv?

---

### Post by klonner on 2008-01-25
Hola ara mateix no tinc ubuntu instalat, però en teoria amb un live CD hauria de funcionar igual aixo no??

amb el Suse m'ha tornat això


lsmod
Module                  Size  Used by
ip6t_LOG               23424  7
nf_conntrack_ipv6      38400  4
xt_pkttype             18688  3
ipt_LOG                23040  8
xt_limit               19840  15
snd_pcm_oss            67456  0
snd_mixer_oss          34176  1 snd_pcm_oss
snd_seq                74992  0
af_packet              57100  2
ip6t_REJECT            22272  3
xt_tcpudp              20096  4
ipt_REJECT             21504  3
xt_state               19328  8
iptable_mangle         19712  0
iptable_nat            24580  0
nf_nat                 37420  1 iptable_nat
iptable_filter         19840  1
ip6table_mangle        19584  0
nf_conntrack_ipv4      28816  6 iptable_nat
nf_conntrack           84188  5 nf_conntrack_ipv6,xt_state,iptable_nat,nf_nat,nf
_conntrack_ipv4
nfnetlink              23224  4 nf_conntrack_ipv6,nf_nat,nf_conntrack_ipv4,nf_co
nntrack
ip_tables              37848  3 iptable_mangle,iptable_nat,iptable_filter
ip6table_filter        19584  1
ip6_tables             31944  3 ip6t_LOG,ip6table_mangle,ip6table_filter
x_tables               37000  11 ip6t_LOG,xt_pkttype,ipt_LOG,xt_limit,ip6t_REJEC
T,xt_tcpudp,ipt_REJECT,xt_state,iptable_nat,ip_tables,ip6_tables
ipv6                  372344  19 nf_conntrack_ipv6,ip6t_REJECT,ip6table_mangle
radeon                135056  2
drm                   113064  3 radeon
cpufreq_conservative    24968  0
cpufreq_userspace      23680  0
cpufreq_powersave      18560  0
powernow_k8            31504  0
apparmor               58672  0
fuse                   62512  4
loop                   36356  0
dm_mod                 77152  0
sn9c102               139140  0
bt878                  28376  0
tuner                  79016  0
tvaudio                42012  0
snd_via82xx            47528  1
bttv                  218420  2 bt878
video_buf              43396  1 bttv
ir_common              53764  1 bttv
compat_ioctl32         25472  2 sn9c102,bttv
i2c_algo_bit           23172  1 bttv
btcx_risc              21640  1 bttv
gameport               32656  1 snd_via82xx
snd_mpu401_uart        25984  1 snd_via82xx
gspca                 651536  0
tveeprom               34576  1 bttv
usbhid                 58160  0
zd1211rw               69000  0
firmware_class         27520  2 bttv,zd1211rw
ieee80211softmac       49792  1 zd1211rw
videodev               44416  4 sn9c102,bttv,gspca
rtc_cmos               25016  0
ieee80211              50376  2 zd1211rw,ieee80211softmac
snd_rawmidi            44544  1 snd_mpu401_uart
shpchp                 50716  0
skge                   58768  0
rtc_core               38156  1 rtc_cmos
hid                    43776  1 usbhid
ieee80211_crypt        23168  1 ieee80211
v4l2_common            36480  6 sn9c102,tuner,tvaudio,bttv,compat_ioctl32,videod
ev
snd_via82xx_modem      33420  0
snd_ac97_codec        130248  2 snd_via82xx,snd_via82xx_modem
ac97_bus               19328  1 snd_ac97_codec
snd_pcm               108680  4 snd_pcm_oss,snd_via82xx,snd_via82xx_modem,snd_ac
97_codec
snd_timer              42632  2 snd_seq,snd_pcm
snd_page_alloc         27280  3 snd_via82xx,snd_via82xx_modem,snd_pcm
serio_raw              24068  0
rtc_lib                19968  1 rtc_core
ohci1394               51272  0
ieee1394              115800  1 ohci1394
i2c_viapro             26008  0
i2c_core               43648  6 tuner,tvaudio,bttv,i2c_algo_bit,tveeprom,i2c_via
pro
pci_hotplug            49396  1 shpchp
sr_mod                 33444  0
button                 26400  0
cdrom                  52392  1 sr_mod
v4l1_compat            28676  2 bttv,videodev
k8temp                 22656  0
hwmon                  20232  1 k8temp
snd_seq_device         25620  2 snd_seq,snd_rawmidi
snd                    84984  13 snd_pcm_oss,snd_mixer_oss,snd_seq,snd_via82xx,s                              nd_mpu401_uart,snd_rawmidi,snd_via82xx_modem,snd_ac97_codec,snd_pcm,snd_timer,sn                              d_seq_device
soundcore              25360  1 snd
ff_memless             22536  1 usbhid
floppy                 79624  0
sg                     53304  0
ehci_hcd               50572  0
uhci_hcd               42144  0
usbcore               155560  7 sn9c102,gspca,usbhid,zd1211rw,ehci_hcd,uhci_hcd
sd_mod                 45824  6
edd                    26760  0
ext3                  156688  1
mbcache                26248  1 ext3
jbd                    89192  1 ext3
fan                    22792  0
pata_via               30212  0
sata_via               29700  4
libata                164096  2 pata_via,sata_via
scsi_mod              176536  4 sr_mod,sg,sd_mod,libata
thermal                34576  0
processor              59592  2 powernow_k8,thermal

---

### Post by patrickfromspain on 2008-01-25
Desde suse, podrias penjar el contingut de dmesg?

---

### Post by klonner on 2008-01-25
dmesg
Linux version 2.6.22.5-31-default (geeko@buildhost) (gcc version 4.2.1 (SUSE Lin
ux)) #1 SMP 2007/09/21 22:29:00 UTC
Command line: root=/dev/disk/by-id/scsi-SATA_Maxtor_6L080M0_L22KABAG-part3 vga=0
x317    resume=/dev/sda4 splash=silent
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000003ffb0000 (usable)
 BIOS-e820: 000000003ffb0000 - 000000003ffc0000 (ACPI data)
 BIOS-e820: 000000003ffc0000 - 000000003fff0000 (ACPI NVS)
 BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
 BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
Entering add_active_range(0, 0, 159) 0 entries of 3200 used
Entering add_active_range(0, 256, 262064) 1 entries of 3200 used
end_pfn_map = 1048576
DMI 2.3 present.
ACPI: RSDP 000FA7C0, 0014 (r0 ACPIAM)
ACPI: RSDT 3FFB0000, 0030 (r1 A M I  OEMRSDT   8000716 MSFT       97)
ACPI: FACP 3FFB0200, 0081 (r1 A M I  OEMFACP   8000716 MSFT       97)
ACPI: DSDT 3FFB03F0, 3A3E (r1  A0036 A0036001        1 MSFT  100000D)
ACPI: FACS 3FFC0000, 0040
ACPI: APIC 3FFB0390, 0052 (r1 A M I  OEMAPIC   8000716 MSFT       97)
ACPI: OEMB 3FFC0040, 003F (r1 A M I  OEMBIOS   8000716 MSFT       97)
Scanning NUMA topology in Northbridge 24
No NUMA configuration found
Faking a node at 0000000000000000-000000003ffb0000
Entering add_active_range(0, 0, 159) 0 entries of 3200 used
Entering add_active_range(0, 256, 262064) 1 entries of 3200 used
Bootmem setup node 0 0000000000000000-000000003ffb0000
Zone PFN ranges:
  DMA             0 ->     4096
  DMA32        4096 ->  1048576
  Normal    1048576 ->  1048576
early_node_map[2] active PFN ranges
    0:        0 ->      159
    0:      256 ->   262064
On node 0 totalpages: 261967
  DMA zone: 56 pages used for memmap
  DMA zone: 1270 pages reserved
  DMA zone: 2673 pages, LIFO batch:0
  DMA32 zone: 3526 pages used for memmap
  DMA32 zone: 254442 pages, LIFO batch:31
  Normal zone: 0 pages used for memmap
ACPI: PM-Timer IO Port: 0x808
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Processor #0 (Bootup-CPU)
ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
ACPI: IRQ0 used by override.
ACPI: IRQ2 used by override.
ACPI: IRQ9 used by override.
Setting APIC routing to flat
Using ACPI (MADT) for SMP configuration information
swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
Allocating PCI resources starting at 50000000 (gap: 40000000:bf780000)
SMP: Allowing 2 CPUs, 1 hotplug CPUs
PERCPU: Allocating 50296 bytes of per cpu data
Built 1 zonelists.  Total pages: 257115
Kernel command line: root=/dev/disk/by-id/scsi-SATA_Maxtor_6L080M0_L22KABAG-part
3 vga=0x317    resume=/dev/sda4 splash=silent
bootsplash: silent mode.
Initializing CPU#0
PID hash table entries: 4096 (order: 12, 32768 bytes)
time.c: Detected 2202.869 MHz processor.
Console: colour dummy device 80x25
Checking aperture...
CPU 0: aperture @ c8000000 size 64 MB
Memory: 1023892k/1048256k available (2050k kernel code, 23976k reserved, 1017k d
ata, 316k init)
Calibrating delay using timer specific routine.. 4410.79 BogoMIPS (lpj=8821589)
Security Framework v1.0.0 initialized
Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
Mount-cache hash table entries: 256
CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
CPU: L2 Cache: 512K (64 bytes/line)
CPU 0/0 -> Node 0
SMP alternatives: switching to UP code
Unpacking initramfs... done
Freeing initrd memory: 4358k freed
ACPI: Core revision 20070126
Parsing all Control Methods:
Table [DSDT](id 0001) - 553 Objects with 51 Devices 147 Methods 25 Regions
 tbxface-0587 [00] tb_load_namespace     : ACPI Tables successfully acquired
evxfevnt-0091 [00] enable                : Transition to ACPI mode successful
Using local APIC timer interrupts.
result 12516323
Detected 12.516 MHz APIC timer.
Brought up 1 CPUs
NET: Registered protocol family 16
ACPI: bus type pci registered
PCI: Using configuration type 1
evgpeblk-0956 [00] ev_create_gpe_block   : GPE 00 to 0F [_GPE] 2 regs on int 0x9
evgpeblk-1052 [00] ev_initialize_gpe_bloc: Found 7 Wake, Enabled 0 Runtime GPEs
in this block
Completing Region/Field/Buffer/Package initialization:..........................
................................................................................
........................
Initialized 24/25 Regions 44/44 Fields 47/47 Buffers 15/16 Packages (562 nodes)
Initializing Device/Processor/Thermal objects by executing _INI methods:
Executed 0 _INI methods requiring 0 _STA executions (examined 55 objects)
ACPI: Interpreter enabled
ACPI: (supports S0 S1 S3 S4 S5)
ACPI: Using IOAPIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (0000:00)
PCI: Probing PCI hardware (bus 00)
PCI: enabled onboard AC97/MC97 devices
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 14 15)
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 14 15)
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 11 14 15)
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 *7 10 11 14 15)
ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
ACPI: bus type pnp registered
pnp: PnP ACPI: found 13 devices
ACPI: ACPI bus type pnp unregistered
PCI: Using ACPI for IRQ routing
PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
PCI: Cannot allocate resource region 0 of device 0000:00:00.0
agpgart: Detected AGP bridge 0
agpgart: AGP aperture is 64M @ 0xc8000000
ACPI: RTC can wake from S4
pnp: 00:07: ioport range 0x680-0x6ff has been reserved
pnp: 00:07: ioport range 0x290-0x297 has been reserved
pnp: 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
pnp: 00:09: iomem range 0xfee00000-0xfee00fff could not be reserved
pnp: 00:09: iomem range 0xfff80000-0xffffffff could not be reserved
pnp: 00:0c: iomem range 0x0-0x9ffff could not be reserved
pnp: 00:0c: iomem range 0xc0000-0xdffff has been reserved
pnp: 00:0c: iomem range 0xe0000-0xfffff could not be reserved
pnp: 00:0c: iomem range 0x100000-0x3ffeffff could not be reserved
PCI: Bridge: 0000:00:01.0
  IO window: e000-efff
  MEM window: fbd00000-fbffffff
  PREFETCH window: d0000000-faffffff
PCI: Setting latency timer of device 0000:00:01.0 to 64
NET: Registered protocol family 2
Time: tsc clocksource has been installed.
IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
TCP established hash table entries: 131072 (order: 9, 3145728 bytes)
TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
TCP: Hash tables configured (established 131072 bind 65536)
TCP reno registered
audit: initializing netlink socket (disabled)
audit(1201310456.356:1): initialized
Total HugeTLB memory allocated, 0
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered (default)
PCI: VIA PCI bridge detected. Disabling DAC.
Boot video device is 0000:01:00.0
vesafb: framebuffer at 0xd0000000, mapped to 0xffffc20000680000, using 6144k, to
tal 16384k
vesafb: mode is 1024x768x16, linelength=2048, pages=9
vesafb: scrolling: redraw
vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
bootsplash 3.1.6-2004/03/31: looking for picture...
bootsplash: silentjpeg size 78436 bytes
bootsplash: ...found (1024x768, 28133 bytes, v3).
Console: switching to colour frame buffer device 124x44
fb0: VESA VGA frame buffer device
Real Time Clock Driver v1.12ac
Non-volatile memory driver v1.2
Linux agpgart interface v0.102 (c) Dave Jones
Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing disabled
serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
PNP: PS/2 controller doesn't have AUX irq; using default 12
serio: i8042 KBD port at 0x60,0x64 irq 1
serio: i8042 AUX port at 0x60,0x64 irq 12
mice: PS/2 mouse device common for all mice
input: AT Translated Set 2 keyboard as /class/input/input0
input: PC Speaker as /class/input/input1
NET: Registered protocol family 1
Freeing unused kernel memory: 316k freed
ACPI Exception (processor_core-0787): AE_NOT_FOUND, Processor Device is not pres
ent [20070126]
SCSI subsystem initialized
libata version 3.00 loaded.
sata_via 0000:00:0f.0: version 2.2
ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 20
sata_via 0000:00:0f.0: routed to hard irq line 10
scsi0 : sata_via
scsi1 : sata_via
ata1: SATA max UDMA/133 cmd 0x000000000001c000 ctl 0x000000000001b802 bmdma 0x00
0000000001a800 irq 20
ata2: SATA max UDMA/133 cmd 0x000000000001b400 ctl 0x000000000001b002 bmdma 0x00
0000000001a808 irq 20
ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
ata1.00: ATA-7: Maxtor 6L080M0, BANC1G10, max UDMA/133
ata1.00: 160086528 sectors, multi 16: LBA NCQ (depth 0/32)
ata1.00: configured for UDMA/133
ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
ata2.00: HPA unlocked: 240119615 -> 240121728, native 240121728
ata2.00: ATA-7: Maxtor 6Y120M0, YAR511W0, max UDMA/133
ata2.00: 240121728 sectors, multi 16: LBA
ata2.00: configured for UDMA/133
scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6L080M0   BANC PQ: 0 ANSI: 5
scsi 1:0:0:0: Direct-Access     ATA      Maxtor 6Y120M0   YAR5 PQ: 0 ANSI: 5
pata_via 0000:00:0f.1: version 0.3.1
ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 20
scsi2 : pata_via
scsi3 : pata_via
ata3: PATA max UDMA/133 cmd 0x00000000000101f0 ctl 0x00000000000103f6 bmdma 0x00
0000000001fc00 irq 14
ata4: PATA max UDMA/133 cmd 0x0000000000010170 ctl 0x0000000000010376 bmdma 0x00
0000000001fc08 irq 15
ata3.00: ATAPI: HL-DT-STDVD-ROM GDR8164B, 0L06, max UDMA/33
ata3.01: ATAPI: HL-DT-ST DVDRAM GSA-4165B, DL03, max UDMA/33
ata3.00: configured for UDMA/33
ata3.01: configured for UDMA/33
scsi 2:0:0:0: CD-ROM            HL-DT-ST DVD-ROM GDR8164B 0L06 PQ: 0 ANSI: 5
scsi 2:0:1:0: CD-ROM            HL-DT-ST DVDRAM GSA-4165B DL03 PQ: 0 ANSI: 5
BIOS EDD facility v0.16 2004-Jun-25, 2 devices found
usbcore: registered new interface driver usbfs
usbcore: registered new interface driver hub
usbcore: registered new device driver usb
USB Universal Host Controller Interface driver v3.0
ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 21
sd 0:0:0:0: [sda] 160086528 512-byte hardware sectors (81964 MB)
sd 0:0:0:0: [sda] Write Protect is off
sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO
 or FUA
sd 0:0:0:0: [sda] 160086528 512-byte hardware sectors (81964 MB)
sd 0:0:0:0: [sda] Write Protect is off
sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO
 or FUA
 sda:<6>uhci_hcd 0000:00:10.0: UHCI Host Controller
uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
uhci_hcd 0000:00:10.0: irq 21, io base 0x0000c400
usb usb1: new device found, idVendor=0000, idProduct=0000
usb usb1: new device strings: Mfr=3, Product=2, SerialNumber=1
usb usb1: Product: UHCI Host Controller
usb usb1: Manufacturer: Linux 2.6.22.5-31-default uhci_hcd
usb usb1: SerialNumber: 0000:00:10.0
usb usb1: configuration #1 chosen from 1 choice
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
 sda1 sda2 sda3 sda4
sd 0:0:0:0: [sda] Attached SCSI disk
sd 1:0:0:0: [sdb] 240121728 512-byte hardware sectors (122942 MB)
sd 1:0:0:0: [sdb] Write Protect is off
sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO
 or FUA
sd 1:0:0:0: [sdb] 240121728 512-byte hardware sectors (122942 MB)
sd 1:0:0:0: [sdb] Write Protect is off
sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO
 or FUA
 sdb:<6>ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.1: UHCI Host Controller
uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
uhci_hcd 0000:00:10.1: irq 21, io base 0x0000c800
usb usb2: new device found, idVendor=0000, idProduct=0000
usb usb2: new device strings: Mfr=3, Product=2, SerialNumber=1
usb usb2: Product: UHCI Host Controller
usb usb2: Manufacturer: Linux 2.6.22.5-31-default uhci_hcd
usb usb2: SerialNumber: 0000:00:10.1
usb usb2: configuration #1 chosen from 1 choice
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
 sdb1
sd 1:0:0:0: [sdb] Attached SCSI disk
ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 21
ehci_hcd 0000:00:10.4: EHCI Host Controller
ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 3
ehci_hcd 0000:00:10.4: irq 21, io mem 0xfbc00000
ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
usb usb3: new device found, idVendor=0000, idProduct=0000
usb usb3: new device strings: Mfr=3, Product=2, SerialNumber=1
usb usb3: Product: EHCI Host Controller
usb usb3: Manufacturer: Linux 2.6.22.5-31-default ehci_hcd
usb usb3: SerialNumber: 0000:00:10.4
usb usb3: configuration #1 chosen from 1 choice
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 8 ports detected
ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.2: UHCI Host Controller
uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
uhci_hcd 0000:00:10.2: irq 21, io base 0x0000d000
usb usb4: new device found, idVendor=0000, idProduct=0000
usb usb4: new device strings: Mfr=3, Product=2, SerialNumber=1
usb usb4: Product: UHCI Host Controller
usb usb4: Manufacturer: Linux 2.6.22.5-31-default uhci_hcd
usb usb4: SerialNumber: 0000:00:10.2
usb usb4: configuration #1 chosen from 1 choice
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected
ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.3: UHCI Host Controller
uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
uhci_hcd 0000:00:10.3: irq 21, io base 0x0000d400
usb usb5: new device found, idVendor=0000, idProduct=0000
usb usb5: new device strings: Mfr=3, Product=2, SerialNumber=1
usb usb5: Product: UHCI Host Controller
usb usb5: Manufacturer: Linux 2.6.22.5-31-default uhci_hcd
usb usb5: SerialNumber: 0000:00:10.3
usb usb5: configuration #1 chosen from 1 choice
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 2 ports detected
swsusp: Marking nosave pages: 000000000009f000 - 0000000000100000
swsusp: Basic memory bitmaps created
usb 3-2: new high speed USB device using ehci_hcd and address 3
swsusp: Basic memory bitmaps freed
Attempting manual resume
usb 3-2: new device found, idVendor=0ace, idProduct=1211
usb 3-2: new device strings: Mfr=16, Product=32, SerialNumber=0
usb 3-2: Product: USB2.0 WLAN
usb 3-2: Manufacturer: ZyDAS
usb 3-2: configuration #1 chosen from 1 choice
kjournald starting.  Commit interval 5 seconds
EXT3 FS on sda3, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
usb 5-1: new full speed USB device using uhci_hcd and address 2
usb 5-1: new device found, idVendor=0c45, idProduct=600d
usb 5-1: new device strings: Mfr=0, Product=1, SerialNumber=0
usb 5-1: Product: USB camera
usb 5-1: configuration #1 chosen from 1 choice
usb 1-1: new low speed USB device using uhci_hcd and address 3
usb 1-1: new device found, idVendor=046d, idProduct=c040
usb 1-1: new device strings: Mfr=1, Product=2, SerialNumber=0
usb 1-1: Product: USB-PS/2 Optical Mouse
usb 1-1: Manufacturer: Logitech
usb 1-1: configuration #1 chosen from 1 choice
sd 0:0:0:0: Attached scsi generic sg0 type 0
sd 1:0:0:0: Attached scsi generic sg1 type 0
scsi 2:0:0:0: Attached scsi generic sg2 type 5
scsi 2:0:1:0: Attached scsi generic sg3 type 5
rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
rtc_cmos: probe of 00:02 failed with error -16
ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 17 (level, low) -> IRQ 17
PCI: Disallowing DAC for device 0000:00:0a.0
skge 1.11 addr 0xfba00000 irq 17 chip Yukon-Lite rev 9
skge eth0: addr 00:13:d4:8a:aa:31
ieee80211_crypt: registered algorithm 'NULL'
ieee80211: 802.11 data/management/control stack, git-1.1.13
ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
usbcore: registered new interface driver hiddev
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:10.0
-1
usbcore: registered new interface driver usbhid
drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Linux video capture interface: v2.00
/usr/src/packages/BUILD/gspcav1-20070110/obj/default/gspca_core.c: USB SPCA5XX c
amera found. SONIX sn9c10[1 2]
/usr/src/packages/BUILD/gspcav1-20070110/obj/default/gspca_core.c: [spca5xx_prob
e:3983] Camera type SN9C
/usr/src/packages/BUILD/gspcav1-20070110/obj/default/gspca_core.c: [spca5xx_getc
apability:1189] maxw 352 maxh 288 minw 160 minh 120
usbcore: registered new interface driver gspca
/usr/src/packages/BUILD/gspcav1-20070110/obj/default/gspca_core.c: gspca driver
01.00.12 registered
sr0: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
Uniform CD-ROM driver Revision: 3.20
sr 2:0:0:0: Attached scsi CD-ROM sr0
Floppy drive(s): fd0 is 1.44M
sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.44
usbcore: registered new interface driver sn9c102
FDC 0 is a post-1991 82077
sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
sr 2:0:1:0: Attached scsi CD-ROM sr1
ACPI: PCI Interrupt 0000:00:07.0[A] -> GSI 16 (level, low) -> IRQ 16
ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[fb800000-fb8007ff]  Max
 Packet=[2048]  IR/IT contexts=[4/8]
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
input: Power Button (FF) as /class/input/input3
ACPI: Power Button (FF) [PWRF]
input: Power Button (CM) as /class/input/input4
ACPI: Power Button (CM) [PWRB]
input: Sleep Button (CM) as /class/input/input5
ACPI: Sleep Button (CM) [SLPB]
ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 22
PCI: Setting latency timer of device 0000:00:11.5 to 64
bttv: driver version 0.9.17 loaded
bttv: using 8 buffers with 2080k (520 pages) each for capture
usb 3-2: reset high speed USB device using ehci_hcd and address 3
PCI: Enabling device 0000:00:11.6 (0000 -> 0001)
ACPI: PCI Interrupt 0000:00:11.6[C] -> GSI 22 (level, low) -> IRQ 22
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d800005317f3]
PCI: Setting latency timer of device 0000:00:11.6 to 64
ACPI: PCI interrupt for device 0000:00:11.6 disabled
VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
bttv: Bt8xx card found (0).
ACPI: PCI Interrupt 0000:00:0e.0[A] -> GSI 19 (level, low) -> IRQ 19
bttv0: Bt878 (rev 17) at 0000:00:0e.0, irq: 19, latency: 64, mmio: 0xcfe00000
bttv0: detected: AVerMedia TVCapture 98 [card=13], PCI subsystem ID is 1461:0004
bttv0: using: AVerMedia TVCapture 98 [card=13,autodetected]
bttv0: gpio: en=00000000, out=00000000 in=00f47ff3 [init]
bttv0: Hauppauge/Voodoo msp34xx: reset line init [11]
bt878 #0 [sw]: Test OK
bttv0: Avermedia eeprom[0x4011]: tuner=5 radio:no remote control:yes
bttv0: using tuner=5
bttv0: i2c: checking for MSP34xx @ 0x80... not found
bttv0: i2c: checking for MSP34xx (alternate address) @ 0x88... not found
bttv0: i2c: checking for TDA9875 @ 0xb0... not found
bttv0: i2c: checking for TDA7432 @ 0x8a... not found
bttv0: i2c: checking for TDA9887 @ 0x86... not found
zd1211rw 3-2:1.0: firmware version 4605
tuner 1-0061: chip found @ 0xc2 (bt878 #0 [sw])
tuner 1-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
tuner 1-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
bttv0: registered device video1
bttv0: registered device vbi0
bttv0: PLL: 28636363 => 35468950 .<6>zd1211rw 3-2:1.0: zd1211 chip 0ace:1211 v43
30 high 00-02-e3 RF2959_RF pa0 g----
.<6>zd1211rw 3-2:1.0: eth1
usbcore: registered new interface driver zd1211rw
 ok
input: bttv IR (card=13) as /class/input/input6
bt878: AUDIO driver version 0.0.0 loaded
bt878: Bt878 AUDIO function found (0).
ACPI: PCI Interrupt 0000:00:0e.1[A] -> GSI 19 (level, low) -> IRQ 19
bt878_probe: card id=[0x41461], Unknown card.
Exiting..
ACPI: PCI interrupt for device 0000:00:0e.1 disabled
bt878: probe of 0000:00:0e.1 failed with error -22
Adding 1293224k swap on /dev/sda4.  Priority:-1 extents:1 across:1293224k
device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: [email]dm-devel@redhat.com[/email]
loop: module loaded
fuse init (API version 7.8)
AppArmor: AppArmor initialized
audit(1201310471.976:2):  type=1505 info="AppArmor initialized" pid=2014
powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3500+ processors (version 2.00.
00)
powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x6
powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x8
powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xa
powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
Marking TSC unstable due to cpufreq changes
Time: acpi_pm clocksource has been installed.
[drm] Initialized drm 1.1.0 20060810
ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[drm] Initialized radeon 1.27.0 20060524 on minor 0
NET: Registered protocol family 10
lo: Disabled Privacy Extensions
Mobile IPv6
ip6_tables: (C) 2000-2006 Netfilter Core Team
ip_tables: (C) 2000-2006 Netfilter Core Team
Netfilter messages via NETLINK v0.30.
nf_conntrack version 0.5.0 (4094 buckets, 32752 max)
agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
skge eth0: enabling interface
ADDRCONF(NETDEV_UP): eth0: link is not ready
NET: Registered protocol family 17
skge eth0: Link is up at 100 Mbps, full duplex, flow control both
ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
audit(1201306891.733:3): audit_pid=3474 old=0 by auid=4294967295
[drm] Setting GART location based on new memory map
[drm] Loading R300 Microcode
[drm] writeback test succeeded in 1 usecs
eth0: no IPv6 routers present
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC= SRC=192.168.1.20 DST=224.0.0.251 LEN=64
TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=44
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC= SRC=192.168.1.20 DST=224.0.0.251 LEN=64              TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=44
/usr/src/packages/BUILD/gspcav1-20070110/obj/default/gspca_core.c: [gspca_set_is             oc_ep:881] ISO EndPoint found 0x81 AlternateSet 8
/usr/src/packages/BUILD/gspcav1-20070110/obj/default/gspca_core.c: [gspca_set_is             oc_ep:881] ISO EndPoint found 0x81 AlternateSet 8
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC= SRC=192.168.1.20 DST=224.0.0.251 LEN=64              TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=44
/usr/src/packages/BUILD/gspcav1-20070110/obj/default/gspca_core.c: [gspca_set_is             oc_ep:881] ISO EndPoint found 0x81 AlternateSet 8
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC= SRC=192.168.1.20 DST=224.0.0.251 LEN=64              TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=44
/usr/src/packages/BUILD/gspcav1-20070110/obj/default/gspca_core.c: [spca50x_isoc             _irq:1084] Non-zero status (-63) in isoc completion handler.
/usr/src/packages/BUILD/gspcav1-20070110/obj/default/gspca_core.c: [spca50x_isoc             _irq:1084] Non-zero status (-18) in isoc completion handler.
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC= SRC=192.168.1.20 DST=224.0.0.251 LEN=64              TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=44
SFW2-INext-DROP-DEFLT-INV IN=eth0 OUT= MAC=00:13:d4:8a:aa:31:00:03:c9:d1:e9:b3:0             8:00 SRC=91.189.94.186 DST=192.168.1.20 LEN=1492 TOS=0x00 PREC=0x00 TTL=253 ID=6             0704 DF PROTO=TCP SPT=80 DPT=9642 WINDOW=1884 RES=0x00 ACK PSH URGP=0 OPT (01010             80A3FFF05CF00006A58)

---

### Post by patrickfromspain on 2008-01-26
be, a ubuntu, en teoria, n'hi haura prou amb carregar el modul bttv amb els parametres card=13 i tuner=5, que es el que fa Suse.

salut!

---

### Post by klonner on 2008-01-26
merci, i com se li diu això?? suposo que card=13 i tuner=5 és d'una llista d'elements compatibles...

---

### Post by patrickfromspain on 2008-01-26
Un cop has instalat ubuntu, has de fer:

sudo modprobe -r bttv
sudo modprobe bttv card=15 tuner=5 i a veure si funciona... Si funciona, ja mirare com es feia per fer-ho permanent.

---

### Post by klonner on 2008-01-26
merci, després l'instal·lo i ho provo!

Salut!

---

### Post by klonner on 2008-01-27
al posar la primera linea em contesta això...
FATAL: Module bttv is in use.

al posar la 2a no diu res...

el TvTime em diu lo de sempre "NO SIGNAL"....
i a la part de baix de la pantalla PAL Unsuported by Sonix sn9c10x + Pas 106 sensor cannot open capture device /dev/video0

Crec que el problema està en que vol intentar accedir al /dev/video0 i aquest deu ser la webcam pel que puc entendre al fer un dmseg

[   35.745922] bttv0: Bt878 (rev 17) at 0000:00:0e.0, irq: 20, latency: 64, mmio: 0xcfe00000
[   35.745931] bttv0: detected: AVerMedia TVCapture 98 [card=13], PCI subsystem ID is 1461:0004
[   35.745934] bttv0: using: AVerMedia TVCapture 98 [card=13,autodetected]
[   35.745966] bttv0: gpio: en=00000000, out=00000000 in=00f47ff3 [init]
[   35.748450] bttv0: Hauppauge/Voodoo msp34xx: reset line init [11]
[   35.773320] bttv0: Avermedia eeprom[0x4011]: tuner=5 radio:no remote control:yes
[   35.773323] bttv0: using tuner=5
[   35.773359] bttv0: i2c: checking for MSP34xx @ 0x80... <6>usbcore: registered new interface driver hiddev
[   36.237260] not found
[   36.237265] bttv0: i2c: checking for MSP34xx (alternate address) @ 0x88... <6>input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
[   36.239207] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:10.0-1
[   36.239223] usbcore: registered new interface driver usbhid
[   36.239226] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   36.346000] input: PC Speaker as /class/input/input3
[   36.522229] hda: ATAPI 52X DVD-ROM drive, 256kB Cache, UDMA(33)
[   36.522236] Uniform CD-ROM driver Revision: 3.20
[   36.580345] not found
[   36.580350] bttv0: i2c: checking for TDA9875 @ 0xb0... <6>hdb: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   36.605603] not found
[   36.605608] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   36.774370] ieee80211_crypt: registered algorithm 'NULL'
[   36.779855] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   36.779859] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   36.956002] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   36.997496] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   36.997586] tuner 0-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[   36.997589] tuner 0-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[   37.024192] bttv0: registered device **video1**

Alguna idea de com canviar-ho (ara estava pensant en reinstalar però amb la webcam desconnectada i després ja mirar de connectar-la un altre cop....) si sóc un pel bruto....

---

### Post by patrickfromspain on 2008-01-27
Proba a desconnectar la webcam i reiniciar amb la webcam desconectada.. a veure si aixi funciona.

---

### Post by klonner on 2008-01-27
desconnectant la webcam amb el tvtime FUNCIONAAA!!!!!!!

el Zapping dona un error pero "funciona" però quan intento entrar al preferencies el programa peta, i el XawTV ja ni l'havia obert.


Ara hauria de buscar la manera de forçar a la tv a ser el video0 i la webcam que fos el video1 no?

---

### Post by patrickfromspain on 2008-01-27
si... proba el kdetv, a mi es el que més m'agradava.

Salut!

---

### Post by klonner on 2008-01-28
com puc fer que la capturadora sigui el /dev/video0 i la webcam /dev/video1 ?

la capturadora és PCI, la webcam USB, alguna manera que registri primer els dispositius pci i després els USB?.

Engengant el PC amb la webcam desconnectada i connectar-la amb el PC funcionant no hi ha problema, webcam OK (era problema de la versió de l'amsn) i la TV tb funciona

---

