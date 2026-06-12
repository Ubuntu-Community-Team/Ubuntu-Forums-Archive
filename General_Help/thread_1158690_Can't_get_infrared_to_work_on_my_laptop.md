---
title: "Can't get infrared to work on my laptop"
date: 2009-05-13
forum: General Help
---

### Post by SoCalChris on 2009-05-13
I've got a Dell Inspiron 9100 that I'm setting up as a MythTV frontend. For the life of me, I can't get infrared to work.

I've verified that it's enabled in the BIOS, and have tried it on COM1-4.

I've found [this guide]("http://datacurrent.blogspot.com/2008/02/comercial-infrared-lirc-on-dell.html") to enabling the infrared port for Gentoo, but am having trouble loading the lirc_sir module that they're recommending. The lirc_dev module is loaded already, so I unload it, and then try loading the lirc_sir module. This reloads the lirc_dev module, but throws out the following error.

```
WARNING: All config files need .conf: /etc/modprobe.d/irda-utils, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Error inserting lirc_sir (/lib/modules/2.6.28-12-generic/kernel/ubuntu/lirc/lirc_sir/lirc_sir.ko): Device or resource busy

```

I'm guessing that this means that there is another module loaded that is using the irda port, but I can't see which one it is.

```
Module                  Size  Used by
isofs                  39844  0 
udf                    87716  0 
crc_itu_t              10112  1 udf
nls_cp437              13696  1 
cifs                  266916  1 
aes_i586               15744  3 
aes_generic            35880  1 aes_i586
ieee80211_crypt_ccmp    13440  3 
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
joydev                 18368  0 
snd_intel8x0           38044  3 
snd_ac97_codec        112292  1 snd_intel8x0
pcmcia                 44748  0 
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd_seq_midi           14336  0 
intel_agp              34108  1 
agpgart                42696  1 intel_agp
snd_rawmidi            29696  1 snd_seq_midi
yenta_socket           32396  1 
psmouse                61972  0 
ipw2200               150984  0 
dcdbas                 15264  0 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
rsrc_nonstatic         19328  1 yenta_socket
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
pcspkr                 10496  0 
serio_raw              13316  0 
ieee80211              38344  1 ipw2200
ieee80211_crypt        13444  2 ieee80211_crypt_ccmp,ieee80211
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
shpchp                 40212  0 
snd                    62628  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm
btusb                  19608  2 
video                  25360  0 
output                 11008  1 video
xfs                   552104  2 
usb_storage            99520  1 
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
b44                    35984  0 
ssb                    41220  1 b44
mii                    13312  1 b44
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```

Any ideas on where to start looking? Thanks

---

### Post by SoCalChris on 2009-05-15
Bumping so the daytime readers see this...

---

