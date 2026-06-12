---
title: "Another Update - Another Broken System"
date: 2009-04-09
forum: General Help
---

### Post by joeyknuccione on 2009-04-09
So, the latest update broke my sound. Nothing new there, I knew I shouldn't let it update, but I did anyway, cause apparently I'm a glutton for punishment.

So, how do I fix my sound?

---

### Post by askreet on 2009-04-09
Going to need some details:

- Do you know what updates you applied?  Anything to 'pulseaudio'?  A new kernel?
- Does your system report that there is no sound device, or are you just  getting no sound?
- Could you try running a sound application from a terminal and capturing some error (or lack of error) output, for example:
$ mplayer futurama_s01e01.avi
- The output of 'lspci' and 'lsmod' as root.

EDIT:  Neat, this was my 100th post!  :)

---

### Post by joeyknuccione on 2009-04-09
> **askreet said:**
> Going to need some details:

- Do you know what updates you applied?  Anything to 'pulseaudio'?  A new kernel?
- Does your system report that there is no sound device, or are you just  getting no sound?
- Could you try running a sound application from a terminal and capturing some error (or lack of error) output, for example:
$ mplayer futurama_s01e01.avi
- The output of 'lspci' and 'lsmod' as root.

EDIT:  Neat, this was my 100th post!  :)

as root lspci = 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

as root lsmod = (not sure what is what, so here's all of it)
Module                  Size  Used by
binfmt_misc            16904  1 
sco                    18308  2 
rfcomm                 44560  0 
bnep                   20480  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 sco,rfcomm,bnep,l2cap
tun                    18948  0 
vboxnetflt             92168  0 
ppdev                  15748  0 
acpi_cpufreq           15500  0 
cpufreq_conservative    14600  0 
cpufreq_ondemand       14988  2 
cpufreq_userspace      11396  0 
cpufreq_powersave       9856  0 
cpufreq_stats          13188  0 
freq_table             12672  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
container              11520  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
pci_slot               12680  0 
af_packet              25728  2 
bridge                 56980  0 
stp                    10628  1 bridge
ipv6                  263972  16 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
vboxdrv               118824  1 vboxnetflt
sbp2                   29324  0 
parport_pc             39332  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
uvcvideo               63752  0 
compat_ioctl32          9344  1 uvcvideo
joydev                 18368  0 
snd_pcm_oss            46496  0 
arc4                    9984  2 
snd_mixer_oss          22784  1 snd_pcm_oss
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
snd_pcm                83844  1 snd_pcm_oss
snd_seq_dummy          11012  0 
r5u870                 32452  0 
usbcam                 50052  1 r5u870
iwl3945                98932  0 
snd_seq_oss            39936  0 
videodev               41344  2 uvcvideo,usbcam
v4l1_compat            22404  2 uvcvideo,videodev
snd_seq_midi           14368  0 
rfkill                 17176  2 iwl3945
videobuf_dma_sg        20612  1 usbcam
snd_rawmidi            29728  1 snd_seq_midi
videobuf_core          26628  2 usbcam,videobuf_dma_sg
psmouse                45200  0 
mac80211              216820  1 iwl3945
serio_raw              13444  0 
sdhci_pci              15360  0 
pcspkr                 10624  0 
evdev                  17696  13 
nvidia               6909268  36 
sdhci                  23940  1 sdhci_pci
led_class              12164  1 iwl3945
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
ricoh_mmc              11904  0 
mmc_core               58268  1 sdhci
i2c_core               31892  1 nvidia
snd_seq                58352  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
cfg80211               32392  2 iwl3945,mac80211
snd_timer              29448  2 snd_pcm,snd_seq
snd_seq_device         15500  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
battery                18436  0 
video                  25232  0 
output                 11008  1 video
snd                    66212  9 snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    14504  0 
iTCO_wdt               18596  0 
ac                     12292  0 
intel_agp              33724  0 
button                 14224  0 
iTCO_vendor_support    11652  1 iTCO_wdt
agpgart                42184  2 nvidia,intel_agp
soundcore              15328  1 snd
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
snd_page_alloc         16776  1 snd_pcm
ext3                  133256  3 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
pata_acpi              12160  0 
sd_mod                 42392  5 
crc_t10dif              9984  1 sd_mod
sg                     39732  2 
ata_piix               24708  0 
usbhid                 35840  0 
hid                    50560  1 usbhid
ata_generic            12932  0 
ahci                   37132  6 
ohci1394               37936  0 
libata                178208  4 pata_acpi,ata_piix,ata_generic,ahci
ieee1394               96324  2 sbp2,ohci1394
scsi_mod              155212  5 sbp2,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
ehci_hcd               43788  0 
uhci_hcd               30864  0 
e1000e                112808  0 
usbcore               149488  7 uvcvideo,r5u870,usbcam,usbhid,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3

---

