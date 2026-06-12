---
title: "Still getting no sound in enemy territory"
date: 2008-03-24
forum: Gaming &amp; Leisure
---

### Post by kelvin911 on 2008-03-24
I still getting no sound in ET  anyone can help?

my config:
asus p5nd2-sli
core dual 3.2GHz
1 GB ram
EVGA 7600 GT 256mb
250 GB SATA HD
i think sound card is realtek on board sound, is that the problem ?

help i want to play et in ubuntu

---

### Post by xeth_delta on 2008-03-24
Two questions. Does sound work with any other programs? Pardon my ignorance, what is ET?

---

### Post by madsmeg on 2008-03-24
I sometimes get problems with ET when i am playing music with certain player, are you using OSS or ALSA for ET? (its Enemy Territory btw xeth_delta)

---

### Post by YldGuy on 2008-03-24
i dont remember the name of the package right now but on the ET (Enemy Territory) website there is one sound package you need to download and install to work.

unfortunately, I cant give you the link because its blocked in office :(. Google it.

---

### Post by Rytron on 2008-03-25
Try this in terminal:

```
sudo killall esd
sudo -i
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
exit
et
```

This works. You may have to do this each time you start ET however.

---

### Post by matoxxx on 2008-03-27
Handy workaround, install it as root and than chmod -R 777 all enemy terrory folders.

---

