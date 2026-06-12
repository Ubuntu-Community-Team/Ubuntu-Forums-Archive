---
title: "No Sound in Americas Army"
date: 2007-09-13
forum: Gaming &amp; Leisure
---

### Post by dean20007 on 2007-09-13
Hi

Ive just installed this and everything seems to be ok except I don't get any sound. Did a bit off searching around the forums and other people hav similar issues except they get told something along lines of

open /dev/[sound/]dsp: Device or resource busy 

when running from terminal. I don't receive any error message like that and sound still plays as normal for other things. When I go to the sound tab in the game it says it using openal (i think?) as the sound device. 

the output from lsmod is below if i can provide anymore details to help with troubleshooting this please just let me know

cheers
```

Module                  Size  Used by
ipv6                  268960  21 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
nfs                   240876  0 
nfsd                  218992  17 
exportfs                6912  1 nfsd
lockd                  64904  3 nfs,nfsd
sunrpc                161340  12 nfs,nfsd,lockd
ppdev                  10116  0 
radeon                124576  3 
drm                    81044  4 radeon
powernow_k8            16064  0 
cpufreq_userspace       5408  0 
cpufreq_ondemand        9228  1 
cpufreq_conservative     8200  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7360  0 
freq_table              5792  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
pcc_acpi               13184  0 
dev_acpi               12292  0 
tc1100_wmi              8068  0 
sony_acpi               6284  0 
ac                      6020  0 
sbs                    15652  0 
asus_acpi              17308  0 
i2c_ec                  6016  1 sbs
i2c_core               22656  1 i2c_ec
backlight               7040  1 asus_acpi
video                  16388  0 
container               5248  0 
button                  8720  0 
battery                10756  0 
dock                   10268  0 
isofs                  36284  0 
udf                    85252  0 
nls_utf8                3072  2 
ntfs                  107764  2 
lp                     12452  0 
fuse                   46612  0 
sn9c102                90892  0 
snd_intel8x0           34332  1 
snd_ac97_codec         98464  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
xpad                    9988  0 
gspca                 607824  0 
snd_usb_audio          79744  0 
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  2 snd_pcm_oss
videodev               28160  2 sn9c102,gspca
v4l2_common            25216  2 sn9c102,videodev
parport_pc             36388  1 
rt73                  214528  0 
usbhid                 26592  0 
snd_pcm                79876  4 snd_intel8x0,snd_ac97_codec,snd_usb_audio,snd_pcm_oss
snd_usb_lib            17280  1 snd_usb_audio
snd_timer              23684  2 snd_seq,snd_pcm
parport                36936  3 ppdev,lp,parport_pc
hid                    27392  1 usbhid
snd_rawmidi            25472  2 snd_seq_midi,snd_usb_lib
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd_hwdep               9988  1 snd_usb_audio
psmouse                38920  0 
pcspkr                  4224  0 
v4l1_compat            15236  1 videodev
serio_raw               7940  0 
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_seq_oss,snd_seq,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_rawmidi,snd_seq_device,snd_hwdep
soundcore               8672  2 snd
k8temp                  6656  0 
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
amd64_agp              13700  1 
sis_agp                 9604  0 
agpgart                35400  3 drm,amd64_agp,sis_agp
af_packet              23816  6 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
tsdev                   8768  0 
evdev                  11008  5 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sd_mod                 23428  5 
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
generic                 5124  0 [permanent]
sata_sis               10500  4 
sis5513                14856  0 [permanent]
floppy                 59524  0 
ehci_hcd               34188  0 
sis900                 24704  0 
mii                     6528  1 sis900
ohci_hcd               22532  0 
usbcore               134280  10 sn9c102,xpad,gspca,snd_usb_audio,rt73,usbhid,snd_usb_lib,ehci_hcd,ohci_hcd
pata_sis               14732  1 sata_sis
ata_generic             9092  0 
libata                125720  3 sata_sis,pata_sis,ata_generic
scsi_mod              142348  4 sd_mod,sg,sr_mod,libata
thermal                14856  0 
processor              31048  2 powernow_k8,thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

```

---

### Post by Velociraptor on 2007-09-13
Open a terminal and enter the following before starting the game:

**  killall esd**

Works for me, I had the same problem.

---

### Post by dean20007 on 2007-09-13
tried that. still no luck

---

### Post by dean20007 on 2007-09-15
If it helps this is the output i get when running the game from terminal
```

Cheat protection disabled
WARNING: ALC_EXT_capture is subject to change!
Defaulting to false
*********************************WARN_ONCE*********************************
File r300_vertexprog.c function valid_dst line 333
Output 3 not used by fragment program
***************************************************************************
*********************************WARN_ONCE*********************************
File radeon_mm.c function radeon_mm_alloc line 216
Ran out of GART memory (for 1048576)!
Please consider adjusting GARTSize option.
***************************************************************************
CTRL-C before main loop ... forcing exit.

```

---

