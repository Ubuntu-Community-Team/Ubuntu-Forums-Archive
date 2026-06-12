---
title: "no sound"
date: 2005-12-12
forum: Desktop Environments
---

### Post by motu on 2005-12-12
hi there !
I've had sound for a while, but since few days it seems something has changed :
no more sound, i've checked a lot of things (module is present, nothing is muted, ...)
but nothing , still no sound.
maybe some updates have misconfig something or i don't know what...it's strange.
is everybody can help please?

thanks in advance

motu 

config:
DELL Computer with AC97 sound card (running alsa)

---

### Post by schdefan on 2005-12-12
check the cable!
post the output of
```
cat /proc/asound/cards
lsusb|grep audio


```what does alsamixer says?

schdefan

---

### Post by motu on 2005-12-12
ok for the cable ;)
outputs :
```
#cat /proc/asound/cards
0 [ICH5           ]: ICH4 - Intel ICH5
                     Intel ICH5 with STAC9750,51 at 0xf8fff800, irq 17
```

no output for the second command...it seems to be normal as the sound card is not usb.

---

### Post by schdefan on 2005-12-13
sorry. I wrote too fast it is not lsusb it is lspci.
and when you open alsamixer did you see the faders?
I found out that sometimes there is a toggle for analog and digital output.

schdefan

---

