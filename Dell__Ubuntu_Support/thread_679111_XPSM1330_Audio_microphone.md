---
title: "XPSM1330 Audio microphone"
date: 2008-01-26
forum: Dell  Ubuntu Support
---

### Post by bimargulies on 2008-01-26
Since I got my M1330, I've been avidly following the many threads that discuss audio issues on this hardware.

I've got the STAC audio that reports to

sudo lspci -nvvv -d 8086:284b

I've installed the latest backport from dell. I still don't seem to have a working built-in microphone.

I fear that one of the previous things I did has lingering ill effects.

Here's my alsa-base file.

options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel model=3stack

I've installed the latest backport posted on Dell's site.

Anyone have any advice?

---

### Post by jdelaros1 on 2008-01-26
Is the Digital Input Source is set to Digital Mic? Also, make sure you unmute and raise the volume of all the alsamixer recording settings.

---

