---
title: "installing onboard sound driver help! where to install??"
date: 2006-08-18
forum: Desktop Environments
---

### Post by WalmartSniperLX on 2006-08-18
I have a via chipset and im trying to install a driver for the audio. I downloaded the linux version and it gave me a package of 3 folders. The 3 are titled:

alsa-driver-1.0.9.tar.bz2
alsa-driver-1.0.9a.tar.bz2
alsa-driver-1.0.9b.tar.bz2

Would I just install one of them or all of them, and where do I install them? sorry I havnt installed motherboard drivers before. Please can anyone help me??? :D

---

### Post by croak77 on 2006-08-19
What is your onboard sound? You said VIA but could you be more specific? You might not have to install anything just modprobe the right module.

---

### Post by WalmartSniperLX on 2006-08-19
It is a VT8233/A/8235/8237 AC97 Audio lol

---

### Post by croak77 on 2006-08-19
I think you want the snd-via82xx module. Open a terminal and type;

```
lsmod
```

And look for snd-via82xx. If it's not there type;

```
sudo modprobe snd-via82xx
```

---

### Post by WalmartSniperLX on 2006-08-20
I just did that but im not sure if its working or if its something else. I am unable to get my mic working. :confused: (and it works lol its not broken and its plugged in the mic port)

---

### Post by croak77 on 2006-08-20
Try opening a terminal and running alsamixer. Mess around with the settings and see which controls the volume on your line in.

---

