---
title: "Americas Army has no sound"
date: 2005-08-02
forum: Gaming &amp; Leisure
---

### Post by umdzig on 2005-08-02
I installed americas army with no problem. However, when i play it i get no sound. My terminal displays this:
[B]
open /dev/[sound/]dsp: Device or resource busy[/B]

What could be causing this and how can i fix it?

---

### Post by amohanty on 2005-08-02
try using alsa instead of oss as the default mixer.

AM

---

### Post by umdzig on 2005-08-02
ok i changed it and still nothing. When i  tested it using the multimedia systems selector it said it failed to construct pipeline. Any ideas?

---

### Post by amohanty on 2005-08-02
Post what 
>> lsmod 
returns.

AM

---

### Post by umdzig on 2005-08-02
[QUOTE=amohanty]Post what 
>> lsmod 
returns.

AM[/QUOTE]
 K here it is:

```
root@laptopmike:~ # lsmod
Module                  Size  Used by
usbhid                 31936  0
binfmt_misc            11496  1
speedstep_centrino      7892  1
proc_intf               3908  0
freq_table              4004  1 speedstep_centrino
cpufreq_userspace       4348  1
cpufreq_ondemand        6140  0
cpufreq_powersave       1632  0
pcmcia                 22244  2
ipt_limit               2368  8
iptable_mangle          2720  0
ipt_LOG                 6880  8
ipt_MASQUERADE          3488  0
iptable_nat            26376  1 ipt_MASQUERADE
ipt_TOS                 2368  0
ipt_REJECT              6848  1
ip_conntrack_irc       71664  0
ip_conntrack_ftp       72528  0
ipt_state               1824  6
ip_conntrack           46420  5 ipt_MASQUERADE,iptable_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
iptable_filter          3584  1
ip_tables              18464  9 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,iptable_nat,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
fglrx                 237088  7
video                  15972  0
sony_acpi               5928  0
pcc_acpi               11008  0
button                  6480  0
battery                 9988  0
container               4320  0
ac                      4676  0
ipv6                  257888  9
af_packet              21992  4
ohci1394               34596  0
yenta_socket           21344  0
pcmcia_core            57984  2 pcmcia,yenta_socket
b44                    21988  0
mii                     4896  1 b44
snd_intel8x0           32352  4
snd_ac97_codec         74144  1 snd_intel8x0
snd_pcm_oss            52132  2
snd_mixer_oss          19680  2 snd_pcm_oss
snd_pcm                94696  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25060  1 snd_pcm
snd                    55012  7 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10016  5 snd
snd_page_alloc          9732  2 snd_intel8x0,snd_pcm
ehci_hcd               32708  0
uhci_hcd               32816  0
pci_hotplug            33488  0
intel_agp              22140  1
agpgart                33608  2 intel_agp
pcspkr                  3496  0
rtc                    12472  0
nls_utf8                1952  1
ntfs                  110512  1
md                     47440  0
dm_mod                 59420  1
capability              4648  0
commoncap               7712  1 capability
evdev                   9344  0
ndiswrapper           120980  0
tsdev                   7520  0
usbcore               119000  5 usbhid,ehci_hcd,uhci_hcd,ndiswrapper
sr_mod                 17188  0
sbp2                   23816  0
scsi_mod              127552  2 sr_mod,sbp2
ieee1394              108312  2 ohci1394,sbp2
mousedev               11288  1
psmouse                21320  0
parport_pc             37252  1
lp                     11144  0
parport                36744  2 parport_pc,lp
ide_cd                 41700  0
cdrom                  40220  2 sr_mod,ide_cd
ext3                  137256  1
jbd                    60536  1 ext3
mbcache                 8356  1 ext3
ide_generic             1312  0
piix                   10340  1
ide_disk               20416  4
ide_core              129356  4 ide_cd,ide_generic,piix,ide_disk
unix                   28276  878
thermal                13320  0
processor              22452  2 speedstep_centrino,thermal
fan                     4388  0
fbcon                  37504  71
font                    8192  1 fbcon
bitblit                 5472  1 fbcon
vesafb                  6724  1
cfbcopyarea             3808  1 vesafb
cfbimgblt               2912  1 vesafb
cfbfillrect             3488  1 vesafb
```

---

