---
title: "Sound problem in Ubuntu 9.0.4 Dell Studio 15"
date: 2010-01-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by svikas on 2010-01-01
Hi,

Problem in audio in Ubuntu 9.0.4 fresh install. We can't hear anything.
Audio in Windows Vista (dual boot) works fine on same laptop.

I've seen this issue being discussed in this forum many times. Unfortunately,
none of the things I tried out worked. Volume is not muted. Changed Audio to
"PulseAudio" also. Modifiled alsa-base.conf by adding following and reboot:

options snd-hda-intel model=6stack-dig
options snd-hda-intel probe_mask=1

$ lsmod
Module                  Size  Used by
isofs                  39844  0 
udf                    87716  0 
crc_itu_t              10112  1 udf
binfmt_misc            16776  1 
ppdev                  15620  0 
radeon                342816  2 
drm                    96296  3 radeon
btusb                  19608  2 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
arc4                    9856  2 
ecb                    10752  2 
iwlagn                100228  0 
iwlcore                93184  1 iwlagn
led_class              12036  1 iwlcore
mac80211              217208  2 iwlagn,iwlcore
snd_hda_intel         435636  3 
cfg80211               38032  3 iwlagn,iwlcore,mac80211
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seqdi,snd_seq
intel_agp              34108  0 
joydev                 18368  0 
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                61972  0 
agpgart                42696  2 drm,intel_agp
dcdbas                 15264  0 
uvcvideo               63240  0 
soundcore              15200  1 snd
ricoh_mmc              11904  0 
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
serio_raw              13316  0 
pcspkr                 10496  0 
iTCO_wdt               19108  0 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
usbhid                 42336  0 
compat_ioctl32          9344  1 uvcvideo
iTCO_vendor_support    11652  1 iTCO_wdt
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
video                  25360  0 
output                 11008  1 video
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
tg3                   131204  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

Please advice...

Thanks and Happy New Year to all...

Regards,
Vikas

---

### Post by Vishnu V on 2010-01-01
Add
```

options snd-hda-intel model=dell-m6

```
to alsa-base.conf and change audio to ALSA

---

### Post by svikas on 2010-01-01
> **Vishnu V said:**
> Add
```

options snd-hda-intel model=dell-m6

```to alsa-base.conf and change audio to ALSA

Vishnu,

Many thanks. Did the changes followed by reboot. Works fine now..

Thanks again for the prompt reply...

Regards,
Vikas

---

