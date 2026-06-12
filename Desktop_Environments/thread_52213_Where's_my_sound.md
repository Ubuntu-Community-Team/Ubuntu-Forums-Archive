---
title: "Where's my sound?"
date: 2005-07-27
forum: Desktop Environments
---

### Post by dr_rude on 2005-07-27
good day,

another questions bout sound? my pc is quite silent after installations. where's my sound? i'm using beep media player but there's no sound at all and same as xmms. it load the file nicely but can't play that file.

i'm issued the following cmd [maybe tis will give you some info].

root@rude:~ # lsmod | grep snd
snd_intel8x0           29984  3
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  2
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  5 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm

root@rude:~ # lspci
0000:00:00.0 Host bridge: Intel Corp. 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 82850 850 (Tehama) Chipset AGP Bridge (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corp. 82801BA ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801BA IDE U100 (rev 02)
0000:00:1f.2 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #1) (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801BA/BAM SMBus (rev 02)
0000:00:1f.4 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #2) (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801BA/BAM AC'97 Audio (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R100 QD [Radeon 7200] (rev 01)
0000:02:0a.0 Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 0c)

---

### Post by pataphysician on 2005-07-27
after installing beep i had to go into preferences | plugins | output tab and chose the esound output plugin. the default i think is OSS and it doesn't seem to work too often.

---

### Post by dr_rude on 2005-07-27
now the files play but without sound?  :???:

---

