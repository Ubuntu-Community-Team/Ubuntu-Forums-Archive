---
title: "Problem with a webcam"
date: 2008-12-28
forum: General Help
---

### Post by Western Digital on 2008-12-28
I have a Sony Vaio AR-1, and I spent a while getting drivers to work for the r5u870 drivers. But finally after getting "modprobe r5u870" to work, I run xawtv and get this:

root@ubuntu:/home/david# xawtv
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.27-9-generic)
xinerama 0: 1440x900+0+0
WARNING: No DGA direct video mode for this display.
/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOC_S_STD(std=0x0 []): Invalid argument

I get a blackscreen from it as well.

Could someone please help me with this? 

Thank you,

David

---

### Post by spiderbatdad on 2008-12-28
please include the output of a couple of commands:
```
lspci
lsusb
lsmod
```

---

### Post by Western Digital on 2008-12-28
I didn't trim any of it out, just in case I accidentally left something out.
```
root@ubuntu:/home/david# lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G86M [GeForce 8400M GT] (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

```

lsusb:

```
root@ubuntu:/home/david# lsusb
Bus 007 Device 004: ID 05ac:1261 Apple, Inc. iPod Classic
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
***** Bus 003 Device 002: ID 05ca:1839 Ricoh Co., Ltd *****
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 1532:0007 Razer USA, Ltd DeathAdder Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

lsmod:

```
root@ubuntu:/home/david# lsmod
Module                  Size  Used by
af_packet              25728  2 
binfmt_misc            16904  1 
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    57376  1 vfat
vboxdrv                71576  0 
sonypi                 26648  0 
ppdev                  15620  0 
vmnet                  48580  13 
vmblock                21156  3 
vmci                   58964  0 
vmmon                  78064  0 
ipv6                  263972  12 
acpi_cpufreq           15500  1 
cpufreq_conservative    14600  0 
cpufreq_ondemand       14988  1 
cpufreq_userspace      11396  0 
cpufreq_stats          13188  0 
cpufreq_powersave       9856  0 
freq_table             12672  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
container              11520  0 
video                  25104  0 
output                 11008  1 video
sbs                    19464  0 
sbshc                  13440  1 sbs
pci_slot               12552  0 
wmi                    14504  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
loop                   23180  0 
uvcvideo               62728  0 
compat_ioctl32          9344  1 uvcvideo
joydev                 18368  0 
pcmcia                 43052  0 
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
snd_hda_intel         381488  4 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
iwlagn                 99588  0 
snd_pcm                83204  3 snd_hda_intel,snd_pcm_oss
iwlcore                92740  1 iwlagn
r5u870                 32452  0 
usbcam                 50180  1 r5u870
rfkill                 17176  2 iwlcore
snd_seq_dummy          10884  0 
videodev               41344  2 uvcvideo,usbcam
led_class              12164  1 iwlcore
v4l1_compat            22404  2 uvcvideo,videodev
tifm_7xx1              13824  0 
snd_seq_oss            38528  0 
mac80211              216820  2 iwlagn,iwlcore
yenta_socket           31756  1 
psmouse                45200  0 
iTCO_wdt               18596  0 
videobuf_dma_sg        20612  1 usbcam
serio_raw              13444  0 
iTCO_vendor_support    11652  1 iTCO_wdt
tifm_core              16028  1 tifm_7xx1
rsrc_nonstatic         19072  1 yenta_socket
pcspkr                 10624  0 
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
evdev                  17696  13 
videobuf_core          26628  2 usbcam,videobuf_dma_sg
snd_seq_midi           14336  0 
nvidia               7103300  56 
cfg80211               32392  3 iwlagn,iwlcore,mac80211
snd_rawmidi            29824  1 snd_seq_midi
i2c_core               31892  1 nvidia
sony_laptop            39004  0 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  3 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
battery                18436  0 
soundcore              15328  1 snd
ac                     12292  0 
button                 14224  0 
intel_agp              33724  0 
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
agpgart                42184  2 nvidia,intel_agp
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
ata_piix               24580  0 
pata_acpi              12160  0 
sd_mod                 42264  5 
crc_t10dif              9984  1 sd_mod
usbhid                 35840  0 
hid                    50560  1 usbhid
sg                     39732  0 
usb_storage            81728  1 
libusual               27156  1 usb_storage
ohci1394               37936  0 
ahci                   37132  2 
ata_generic            12932  0 
ieee1394               96324  2 sbp2,ohci1394
libata                177312  4 ata_piix,pata_acpi,ahci,ata_generic
scsi_mod              155212  6 sbp2,sr_mod,sd_mod,sg,usb_storage,libata
dock                   16656  1 libata
ehci_hcd               43276  0 
sky2                   53380  0 
uhci_hcd               30736  0 
usbcore               148848  9 uvcvideo,r5u870,usbcam,usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

```

Thanks for reply

---

### Post by spiderbatdad on 2008-12-28
so...I'm no expert but it doesn't look like your modules are loaded. I'm thinking try these one at a time:
```

sudo modprobe r5u870
sudo modprobe videodev
sudo modprobe video-buf
sudo modprobe v4l1 compat
sudo modprobe v4l2-common
sudo depmod -a

```
Then reboot your machine and run lsmod again.
Edit: yes they are...I'm just half-blind

---

### Post by Western Digital on 2008-12-28
```
Module                  Size  Used by
af_packet              25728  4 
binfmt_misc            16904  1 
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
nls_iso8859_1          12032  0 
nls_cp437              13696  0 
vfat                   18816  0 
fat                    57376  1 vfat
vboxdrv                71576  0 
sonypi                 26648  0 
ppdev                  15620  0 
vmnet                  48580  13 
vmblock                21156  3 
vmci                   58964  0 
vmmon                  78064  0 
ipv6                  263972  12 
acpi_cpufreq           15500  1 
cpufreq_conservative    14600  0 
cpufreq_ondemand       14988  1 
cpufreq_userspace      11396  0 
cpufreq_stats          13188  0 
cpufreq_powersave       9856  0 
freq_table             12672  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
container              11520  0 
video                  25104  0 
output                 11008  1 video
sbs                    19464  0 
sbshc                  13440  1 sbs
pci_slot               12552  0 
wmi                    14504  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
loop                   23180  0 
uvcvideo               62728  0 
compat_ioctl32          9344  1 uvcvideo
joydev                 18368  0 
pcmcia                 43052  0 
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
snd_hda_intel         381488  4 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
iwlagn                 99588  0 
snd_seq_oss            38528  0 
r5u870                 32452  0 
iwlcore                92740  1 iwlagn
usbcam                 50180  1 r5u870
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
rfkill                 17176  2 iwlcore
videodev               41344  2 uvcvideo,usbcam
v4l1_compat            22404  2 uvcvideo,videodev
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcspkr                 10624  0 
yenta_socket           31756  1 
videobuf_dma_sg        20612  1 usbcam
iTCO_wdt               18596  0 
psmouse                45200  0 
tifm_7xx1              13824  0 
rsrc_nonstatic         19072  1 yenta_socket
iTCO_vendor_support    11652  1 iTCO_wdt
led_class              12164  1 iwlcore
videobuf_core          26628  2 usbcam,videobuf_dma_sg
serio_raw              13444  0 
sony_laptop            39004  0 
tifm_core              16028  1 tifm_7xx1
evdev                  17696  13 
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
mac80211              216820  2 iwlagn,iwlcore
nvidia               7103300  56 
snd_timer              29960  3 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cfg80211               32392  3 iwlagn,iwlcore,mac80211
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
battery                18436  0 
i2c_core               31892  1 nvidia
button                 14224  0 
ac                     12292  0 
intel_agp              33724  0 
agpgart                42184  2 nvidia,intel_agp
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
ata_piix               24580  0 
pata_acpi              12160  0 
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
usbhid                 35840  0 
hid                    50560  1 usbhid
sg                     39732  0 
usb_storage            81728  0 
libusual               27156  1 usb_storage
ohci1394               37936  0 
ahci                   37132  2 
ata_generic            12932  0 
ieee1394               96324  2 sbp2,ohci1394
libata                177312  4 ata_piix,pata_acpi,ahci,ata_generic
scsi_mod              155212  6 sbp2,sr_mod,sd_mod,sg,usb_storage,libata
dock                   16656  1 libata
sky2                   53380  0 
ehci_hcd               43276  0 
uhci_hcd               30736  0 
usbcore               148848  9 uvcvideo,r5u870,usbcam,usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

```

---

### Post by spiderbatdad on 2008-12-28
so has it worked? if not try preload like this:
```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so xawtv
```

---

### Post by Western Digital on 2008-12-28
Still not working. I get this:

> oot@ubuntu:/home/david# LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so xawtv
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.27-9-generic)
xinerama 0: 1440x900+0+0
WARNING: No DGA direct video mode for this display.
/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOC_S_STD(std=0x0 []): Invalid argument


For the record, the light on the camera comeso n.

---

### Post by Western Digital on 2008-12-29
bump

---

