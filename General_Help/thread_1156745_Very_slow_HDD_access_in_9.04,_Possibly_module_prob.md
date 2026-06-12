---
title: "Very slow HDD access in 9.04, Possibly module problem?"
date: 2009-05-12
forum: General Help
---

### Post by Shamem on 2009-05-12
Ever since i installed 9.04 last week, it has been plagued with speed problems. The main remaining one is horrible slow disk access(6 minute boots, minute first start times for most apps, etc).

```
sudo hdparm -Tt /dev/sdb

/dev/sdb:
 Timing cached reads:   558 MB in  2.00 seconds = 278.74 MB/sec
 Timing buffered disk reads:    8 MB in  3.20 seconds =   2.50 MB/sec
```

After looking around at some other threads, i found it might be being caused by using the wrong kernel modules to handle the hdd's. However, i can't find anything that looks like a pata/sata modules loaded at all(based on what others are using, and reading the names).

```
lsmod
Module                  Size  Used by
binfmt_misc            16776  1 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
video                  25360  0 
output                 11008  1 video
lp                     17156  0 
snd_hda_intel         434484  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_seq_dummy          10756  0 
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
psmouse                61972  0 
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  15620  0 
joydev                 18368  0 
fglrx                2082308  27 
i2c_ali15x3            14724  0 
i2c_ali1535            14212  0 
serio_raw              13316  0 
pcspkr                 10496  0 
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
k8temp                 12416  0 
shpchp                 40212  0 
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
usbhid                 42336  0 
ati_agp                14988  0 
agpgart                42696  2 fglrx,ati_agp
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
skge                   48272  0 
8139too                32128  0 
8139cp                 27776  0 
mii                    13312  2 8139too,8139cp
floppy                 64324  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```

Anyone have ideas on this?
My hdd's are SATA2 Seagate Barracudas, running in Emulated PATA mode on a Asus A8R-MVP Mobo.

Thanks,

---Shamem

---

