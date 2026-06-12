---
title: "dell, bash kernal wifi problems, please check my dmesg"
date: 2009-03-28
forum: General Help
---

### Post by hubcity on 2009-03-28
i don't understand ubuntu enough yet to know what the problem is, but i know it's there.  i just don't know what is right, in order to compare it to whats wrong.

ive found some commands for terminal to get information, probably too much, but i hope some one can help me get to the {root} of the problem...do you see anything that looks wrong down there?  (i mean below...)

in addition to my wireless connection being...a pain(i am constantly having manually enter all the connection info, plus the pass key, every time 
it fails...for no apparent reason, even though my other laptop, with windows, doesn't disconnect)...i have a bigger issue with, after a few days, at the boot, while ubuntu is loading (or thinking)  it'll get part way through the bar, stop, and give me a message that it need to do a disk check, or system...  not sure which, it catches me off guard, and i really have no experience with bios...but thats where it goes.  does a bunch of checking on bash files, then tells me the test failed, and i must manually do a fschk.  which i do, and we loop through the whole process again, only with different number strings...it all eventually leads to frustration and inserting the cd and reloading, and repartioning...complete, all over a again.  i know im doing something wrong.  just not sure what.

 

thanks for the time..jim

i have a dell latitude d52o, with hardy.  previousle, i had intrepid (which didn't work) and 7.10.  when loaded, i did a complete load, not a repartitioning...i hope i phrased that right.  i didn't keep any of the previoous files.

 ```
 jim@jim-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
02:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```

```
jim@jim-laptop:~$ lsusb
Bus 005 Device 002: ID 413c:a005 Dell Computer Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```
 
```
jim@jim-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:b9:76:b3:73  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1500 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1500 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:75000 (73.2 KB)  TX bytes:75000 (73.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:29:a5:34  
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:77ff:fe29:a534/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5226 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3651 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5563554 (5.3 MB)  TX bytes:596844 (582.8 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-77-29-A5-34-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

jim@jim-laptop:~$ $ iwconfig
bash: $: command not found
jim@jim-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"centralia perk"  Nickname:""
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:0F:66:46:FB:08   
          Bit Rate=5.5 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=38/100  Signal level=-86 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
jim@jim-laptop:~$ lsmod
Module                  Size  Used by
af_packet              23812  4 
ipv6                  267780  10 
i915                   32512  2 
drm                    82452  3 i915
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
acpi_cpufreq           10796  1 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  1 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0 
bay                     6912  0 
dock                   11280  1 bay
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
pcmcia                 40876  0 
joydev                 13120  0 
dcdbas                  9504  0 
serio_raw               7940  0 
yenta_socket           27276  1 
evdev                  13056  7 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                40336  0 
pcspkr                  4224  0 
iwl3945                89844  0 
snd_hda_intel         344728  3 
iwlwifi_mac80211      219108  1 iwl3945
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
cfg80211               15112  1 iwlwifi_mac80211
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
video                  19856  0 
output                  4736  1 video
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
wmi_acer                9644  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                  9232  0 
battery                14212  0 
intel_agp              25492  1 
ac                      6916  0 
soundcore               8800  1 snd
agpgart                34760  3 drm,intel_agp
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
pata_acpi               8320  0 
ata_piix               19588  2 
b44                    28432  0 
ata_generic             8324  0 
libata                159344  3 pata_acpi,ata_piix,ata_generic
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ohci1394               33584  0 
ssb                    34308  1 b44
ieee1394               93752  2 sbp2,ohci1394
mii                     6400  1 b44
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  3 ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 

```

dmesg```
[   21.581638] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   21.582000] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   21.642616] Yenta: ISA IRQ mask 0x0cb8, PCI irq 18
[   21.642620] Socket status: 30000006
[   21.642622] Yenta: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   21.642627] pcmcia: parent PCI bridge Memory window: 0xefc00000 - 0xefcfffff
[   21.876565] cs: IO port probe 0x100-0x3af: clean.
[   21.878537] cs: IO port probe 0x3e0-0x4ff: clean.
[   21.879351] cs: IO port probe 0x820-0x8ff: clean.
[   21.880019] cs: IO port probe 0xc00-0xcf7: excluding 0xc80-0xc87 0xc90-0xc97
[   21.880817] cs: IO port probe 0xa00-0xaff: clean.
[   21.999590] lp: driver loaded but no devices found
[   22.124438] Adding 2441840k swap on /dev/sda5.  Priority:-1 extents:1 across:2441840k
[   22.415546] EXT3 FS on sda1, internal journal
[   23.246157] ip_tables: (C) 2000-2006 Netfilter Core Team
[   24.036561] ACPI: ACPI Dock Station Driver 
[   25.960235] ACPI: \_SB_.PCI0.IDE0.SEC0.MAST: found ejectable bay
[   25.960240] ACPI: \_SB_.PCI0.IDE0.SEC0.MAST: Adding notify handler
[   25.960270] ACPI: Error installing bay notify handler
[   25.960274] ACPI: Bay [\_SB_.PCI0.IDE0.SEC0.MAST] Added
[   24.896133] apm: BIOS not found.
[   27.383665] ppdev: user-space parallel port driver
[   27.521190] audit(1238275453.530:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5165 profile="/usr/sbin/cupsd" namespace="default"
[   26.888826] Bluetooth: Core ver 2.11
[   26.889204] NET: Registered protocol family 31
[   26.889209] Bluetooth: HCI device and connection manager initialized
[   26.889215] Bluetooth: HCI socket layer initialized
[   26.940342] Bluetooth: L2CAP ver 2.9
[   26.940349] Bluetooth: L2CAP socket layer initialized
[   27.015667] Bluetooth: RFCOMM socket layer initialized
[   27.015797] Bluetooth: RFCOMM TTY layer initialized
[   27.015800] Bluetooth: RFCOMM ver 1.8
[   30.522053] [drm] Initialized drm 1.1.0 20060810
[   30.525781] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   30.525793] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   30.526274] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   39.594386] NET: Registered protocol family 10
[   39.595116] lo: Disabled Privacy Extensions
[   39.596919] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   39.598085] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   47.588917] CPU0 attaching NULL sched-domain.
[   47.588923] CPU1 attaching NULL sched-domain.
[   47.609707] CPU0 attaching sched-domain:
[   47.609713]  domain 0: span 03
[   47.609716]   groups: 01 02
[   47.609720] CPU1 attaching sched-domain:
[   47.609723]  domain 0: span 03
[   47.609725]   groups: 02 01
[   56.087003] NET: Registered protocol family 17
[   66.655624] wlan0: Initial auth_alg=1
[   66.655633] wlan0: authenticate with AP 00:0f:66:46:fb:08
[   64.734621] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=2 status=0)
[   64.734628] wlan0: replying to auth challenge
[   64.735447] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=4 status=0)
[   64.735453] wlan0: authenticated
[   64.735457] wlan0: associate with AP 00:0f:66:46:fb:08
[   64.736654] wlan0: RX AssocResp from 00:0f:66:46:fb:08 (capab=0x411 status=0 aid=7)
[   64.736660] wlan0: associated
[   64.740216] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   65.507958] wlan0: no IPv6 routers present
[   69.074185] wlan0: deauthenticate(reason=3)
[   68.214903] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.214910] wlan0: deauthenticated
[   68.214917] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.214922] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.214928] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.214933] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.214938] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215000] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215006] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215011] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215017] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215022] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215027] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215032] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215037] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215043] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215048] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215053] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215058] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215063] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215068] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215074] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215079] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215085] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215090] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215095] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215100] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215105] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215111] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215116] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215121] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215126] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215132] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215137] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215142] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215147] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215152] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215157] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215163] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215168] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215173] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215178] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215183] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215188] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215193] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215198] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215204] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215209] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215214] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215220] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215225] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215230] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215236] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215241] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215246] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215251] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215257] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215262] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215267] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215272] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215277] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215282] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215287] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215293] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215298] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215303] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215309] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215314] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215319] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215324] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215329] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215335] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215340] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215345] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215351] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215356] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215362] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215367] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215374] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215379] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215385] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215390] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215396] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215402] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215408] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215414] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215420] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215426] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215432] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215438] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215451] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215457] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215463] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215468] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215474] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215480] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215486] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215493] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215499] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215505] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215511] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215517] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215523] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215529] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215535] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215541] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215546] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215552] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215558] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215564] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215570] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215575] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215581] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215587] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215594] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215601] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215607] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215613] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215620] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215626] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215632] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215644] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215650] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215656] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215662] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215668] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215673] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215679] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215684] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215690] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215695] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215701] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215707] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215713] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215718] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215724] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215730] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215736] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215742] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215748] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215754] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215760] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215766] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215772] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215778] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215783] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215789] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215795] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215801] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215806] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215812] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215818] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215830] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215836] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215842] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215847] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215853] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215859] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215865] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215871] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215877] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215883] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215889] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215895] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215902] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215908] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215914] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215920] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215926] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215932] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215939] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215945] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215951] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215957] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215963] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215969] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215975] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215982] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215988] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215994] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.215999] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.216005] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.216011] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.216021] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.216027] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.216033] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.216039] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.216045] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.216051] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.216057] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.216063] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.216069] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.216075] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.216080] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.216086] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.216092] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.216098] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.216104] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.216110] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.216116] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.216121] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.216127] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.216133] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.216139] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.216145] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.216151] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.216156] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.216162] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.216168] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.216174] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=7)
[   68.216180] wlan0: authenticate with AP 00:0f:66:46:fb:08
[   68.216205] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   68.219555] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=2 status=0)
[   68.219561] wlan0: replying to auth challenge
[   70.144930] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=6)
[   68.226277] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=4 status=15)
[   68.226283] wlan0: AP denied authentication (auth_alg=1 code=15)
[   70.246558] wlan0: authenticate with AP 00:0f:66:46:fb:08
[   70.246594] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   68.325666] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=2 status=0)
[   68.325674] wlan0: replying to auth challenge
[   68.326898] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=2 status=0)
[   68.326904] wlan0: unexpected authentication frame (alg=1 transaction=2)
[   68.328678] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=2 status=0)
[   68.328684] wlan0: unexpected authentication frame (alg=1 transaction=2)
[   68.331252] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=6)
[   68.332064] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=4 status=15)
[   68.332071] wlan0: AP denied authentication (auth_alg=1 code=15)
[   68.416865] wlan0: Initial auth_alg=1
[   68.416875] wlan0: authenticate with AP 00:0f:66:46:fb:08
[   68.416906] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   68.419174] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=2 status=0)
[   68.419181] wlan0: replying to auth challenge
[   68.421021] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=2 status=0)
[   68.421028] wlan0: unexpected authentication frame (alg=1 transaction=2)
[   68.422983] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=6)
[   68.423779] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=4 status=15)
[   68.423787] wlan0: AP denied authentication (auth_alg=1 code=15)
[   68.482887] wlan0: authenticate with AP 00:0f:66:46:fb:08
[   68.482923] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   68.484726] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=6)
[   68.486021] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=6)
[   68.540370] wlan0: authenticate with AP 00:0f:66:46:fb:08
[   68.540404] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   68.541594] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=6)
[   68.542294] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=6)
[   68.602321] wlan0: Initial auth_alg=1
[   68.602330] wlan0: authenticate with AP 00:0f:66:46:fb:08
[   68.605036] wlan0: Initial auth_alg=1
[   68.605045] wlan0: authenticate with AP 00:0f:66:46:fb:08
[   68.605068] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=2 status=0)
[   68.605073] wlan0: replying to auth challenge
[   68.608076] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=2 status=0)
[   68.608085] wlan0: unexpected authentication frame (alg=1 transaction=2)
[   68.608909] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=4 status=15)
[   68.608917] wlan0: AP denied authentication (auth_alg=1 code=15)
[   68.611170] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=4 status=14)
[   68.611177] wlan0: AP denied authentication (auth_alg=1 code=14)
[   68.622172] wlan0: authenticate with AP 00:0f:66:46:fb:08
[   68.623477] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=2 status=0)
[   68.623486] wlan0: replying to auth challenge
[   68.626121] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=4 status=0)
[   68.626184] wlan0: authenticated
[   68.626188] wlan0: associate with AP 00:0f:66:46:fb:08
[   68.628042] wlan0: RX AssocResp from 00:0f:66:46:fb:08 (capab=0x411 status=0 aid=7)
[   68.628049] wlan0: associated
[   68.631685] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   68.634829] wlan0: association frame received from 00:0f:66:46:fb:08, but not in associate state - ignored
[   69.541339] wlan0: no IPv6 routers present
[   71.676001] wlan0: deauthenticate(reason=3)
[   70.090758] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   70.091451] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=6)
[   70.091456] wlan0: deauthenticated
[   70.093109] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=6)
[   72.153604] wlan0: Initial auth_alg=1
[   72.153614] wlan0: authenticate with AP 00:0f:66:46:fb:08
[   72.153636] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   72.156078] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=2 status=0)
[   72.156087] wlan0: replying to auth challenge
[   72.157916] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=2 status=0)
[   72.157923] wlan0: unexpected authentication frame (alg=1 transaction=2)
[   70.237221] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=6)
[   70.239195] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=6)
[   70.240001] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=4 status=15)
[   70.240008] wlan0: AP denied authentication (auth_alg=1 code=15)
[   70.345194] wlan0: authenticate with AP 00:0f:66:46:fb:08
[   70.345228] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   70.348201] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=6)
[   70.348931] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=6)
[   70.822945] wlan0: authenticate with AP 00:0f:66:46:fb:08
[   70.822980] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   70.824529] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=6)
[   70.826459] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=6)
[   70.940961] wlan0: Initial auth_alg=1
[   70.940971] wlan0: authenticate with AP 00:0f:66:46:fb:08
[   70.943609] wlan0: Initial auth_alg=1
[   70.943624] wlan0: authenticate with AP 00:0f:66:46:fb:08
[   70.943646] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=2 status=0)
[   70.943651] wlan0: replying to auth challenge
[   70.947624] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=2 status=0)
[   70.947633] wlan0: unexpected authentication frame (alg=1 transaction=2)
[   70.950497] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=2 status=0)
[   70.950506] wlan0: unexpected authentication frame (alg=1 transaction=2)
[   70.951934] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=4 status=15)
[   70.951940] wlan0: AP denied authentication (auth_alg=1 code=15)
[   70.986783] wlan0: authenticate with AP 00:0f:66:46:fb:08
[   70.987796] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=2 status=0)
[   70.987806] wlan0: replying to auth challenge
[   70.988726] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=4 status=0)
[   70.988733] wlan0: authenticated
[   70.988737] wlan0: associate with AP 00:0f:66:46:fb:08
[   70.990329] wlan0: authentication frame received from 00:0f:66:46:fb:08, but not in authenticate state - ignored
[   70.991318] wlan0: RX AssocResp from 00:0f:66:46:fb:08 (capab=0x411 status=0 aid=7)
[   70.991324] wlan0: associated
[   70.994920] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   70.998988] wlan0: association frame received from 00:0f:66:46:fb:08, but not in associate state - ignored
[   71.956127] wlan0: no IPv6 routers present
[   72.681545] wlan0: deauthenticate(reason=3)
[   72.764240] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   72.765562] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=6)
[   72.765567] wlan0: deauthenticated
[   72.767080] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=6)
[   74.872856] wlan0: authenticate with AP 00:0f:66:46:fb:08
[   74.872878] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   74.877132] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=6)
[   74.877476] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=6)
[   74.897945] wlan0: Initial auth_alg=1
[   74.897955] wlan0: authenticate with AP 00:0f:66:46:fb:08
[   74.897978] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   74.899076] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=2 status=0)
[   74.899084] wlan0: replying to auth challenge
[   74.899984] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=2 status=0)
[   74.899991] wlan0: unexpected authentication frame (alg=1 transaction=2)
[   74.901046] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=6)
[   74.902489] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=6)
[   74.903259] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=4 status=15)
[   74.903267] wlan0: AP denied authentication (auth_alg=1 code=15)
[   75.028736] wlan0: authenticate with AP 00:0f:66:46:fb:08
[   75.028771] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   73.109372] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=2 status=0)
[   73.109381] wlan0: replying to auth challenge
[   73.110169] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=6)
[   73.111503] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=4 status=15)
[   73.111510] wlan0: AP denied authentication (auth_alg=1 code=15)
[   73.229110] wlan0: authenticate with AP 00:0f:66:46:fb:08
[   73.229144] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   73.231970] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=2 status=0)
[   73.231978] wlan0: replying to auth challenge
[   73.234973] wlan0: RX deauthentication from 00:0f:66:46:fb:08 (reason=6)
[   73.236390] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=4 status=15)
[   73.236397] wlan0: AP denied authentication (auth_alg=1 code=15)
[   75.278726] wlan0: Initial auth_alg=1
[   75.278735] wlan0: authenticate with AP 00:0f:66:46:fb:08
[   73.357908] wlan0: Initial auth_alg=1
[   73.357915] wlan0: authenticate with AP 00:0f:66:46:fb:08
[   73.359732] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=2 status=0)
[   73.359739] wlan0: replying to auth challenge
[   73.365470] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=2 status=0)
[   73.365479] wlan0: unexpected authentication frame (alg=1 transaction=2)
[   75.288913] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=2 status=0)
[   75.288920] wlan0: unexpected authentication frame (alg=1 transaction=2)
[   75.289813] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=4 status=15)
[   75.289820] wlan0: AP denied authentication (auth_alg=1 code=15)
[   75.297480] wlan0: authenticate with AP 00:0f:66:46:fb:08
[   73.377006] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=2 status=0)
[   73.377013] wlan0: replying to auth challenge
[   73.379299] wlan0: RX authentication from 00:0f:66:46:fb:08 (alg=1 transaction=4 status=0)
[   73.379305] wlan0: authenticated
[   73.379309] wlan0: associate with AP 00:0f:66:46:fb:08
[   73.381638] wlan0: RX AssocResp from 00:0f:66:46:fb:08 (capab=0x411 status=0 aid=5)
[   73.381647] wlan0: associated
[   73.385759] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   79.842481] wlan0: no IPv6 routers present

```

```
jim@jim-laptop:~$ sudo lshw -C network
[sudo] password for jim: 
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:77:29:a5:34
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.107 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:76:b3:73
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s

```

```
jim@jim-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results


```

```
jim@jim-laptop:~$ uname -mr
2.6.24-19-generic i686

```

```
jim@jim-laptop:~$ sudo /etc/init.d/networking restart
[sudo] password for jim: 
 * Reconfiguring network interfaces...                                   [ OK ] 

```

---

### Post by hubcity on 2009-03-29
info?

---

