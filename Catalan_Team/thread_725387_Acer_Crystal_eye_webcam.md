---
title: "Acer Crystal eye webcam"
date: 2008-03-15
forum: Catalan Team
---

### Post by Naqash on 2008-03-15
Hola !

Estic utilitzant UBUNTU 7.10,
Tinc Acer 5720, Core2Dou, mobile intel graphics x3100.
Tinc problema amb crystal eye webcam no esta funcionat,  &#65279;Intentava executar-lo amb Ekiga però no funcionava.

Sortida de Ekiga es com aixo,

[[IMG]http://img292.imageshack.us/img292/7716/screenshotkw1.th.png[/IMG]](http://img292.imageshack.us/my.php?image=screenshotkw1.png)

&#65279;La sortida de 1smod és

Module                  Size  Used by
ipv6                  273892  10 
xt_limit                3584  8 
xt_tcpudp               4224  10 
ipt_LOG                 7552  8 
ipt_MASQUERADE          4608  0 
ipt_TOS                 3200  0 
ipt_REJECT              5760  1 
nf_conntrack_irc        8088  0 
nf_conntrack_ftp       11136  0 
xt_state                3456  6 
arc4                    2944  2 
ecb                     4608  2 
blkcipher               7556  1 ecb
ieee80211_crypt_wep     6272  1 
af_packet              24840  4 
i915                   25856  3 
drm                    83348  4 i915
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
acpi_cpufreq           10568  1 
cpufreq_powersave       2688  0 
cpufreq_conservative     8072  0 
cpufreq_userspace       5280  0 
cpufreq_ondemand        9612  1 
cpufreq_stats           7232  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
button                  8976  0 
sbs                    19592  0 
ac                      6148  0 
video                  18060  0 
dock                   10656  0 
container               5504  0 
battery                11012  0 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
joydev                 11328  0 
snd_hda_intel         291488  4 
snd_hwdep              10244  1 snd_hda_intel
snd_pcm_oss            43008  0 
snd_pcm                80004  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_mixer_oss          17664  1 snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53360  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               57480  1 
snd                    54788  16 snd_hda_intel,snd_hwdep,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
compat_ioctl32          2304  1 uvcvideo
videodev               29312  2 uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
v4l2_common            18432  2 uvcvideo,videodev
ipw3945               119840  1 
sdhci                  18828  0 
serio_raw               8068  0 
soundcore               8800  1 snd
mmc_core               28420  1 sdhci
ieee80211              35656  1 ipw3945
ieee80211_crypt         7040  2 ieee80211_crypt_wep,ieee80211
psmouse                39952  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
intel_agp              25620  1 
agpgart                35016  3 drm,intel_agp
evdev                  11136  6 
iptable_nat             8708  0 
nf_nat                 20140  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19724  8 iptable_nat
nf_conntrack           65288  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nfnetlink               6936  3 nf_nat,nf_conntrack_ipv4,nf_conntrack
iptable_mangle          3840  0 
iptable_filter          3968  1 
ip_tables              13924  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               16260  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,iptable_nat,ip_tables
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
usbhid                 29536  0 
hid                    28928  1 usbhid
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sd_mod                 30336  6 
ata_generic             8452  0 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
tg3                   110980  0 
ahci                   23300  5 
ata_piix               17540  0 
libata                125168  3 ata_generic,ahci,ata_piix
scsi_mod              147084  5 sbp2,sg,sr_mod,sd_mod,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  5 uvcvideo,usbhid,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  7 
apparmor               40728  0 
commoncap               8320  1 apparmor


Podeu ajudar-me ?

I perdona per el meu català, encara no puc parlar molt bé.

---

### Post by papapep on 2008-03-15
Benvingut Naqash,

Enganxan's el resultat de fer un

```
lsusb
```

i un

```
lspci
```

si us plau.

EDITO:

Tot el que es troba, en una primera búsqueda ràpida a internet, és que s'ha de compilar el mòdul:

[http://www.universodigital.cl/?p=33](http://www.universodigital.cl/?p=33)

i una altra:

[http://alfredo.perseum.com/blog/tag/acer-crystal-eye-webcam-ubuntu-gutsy-710/](http://alfredo.perseum.com/blog/tag/acer-crystal-eye-webcam-ubuntu-gutsy-710/)

---

