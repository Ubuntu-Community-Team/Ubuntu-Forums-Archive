---
title: "How do I set the default ALSA sound device?"
date: 2006-07-14
forum: Desktop Environments
---

### Post by scotty64 on 2006-07-14
How can I tell ALSA to use the built in soundcard as default device?
Unfortunately my system always defaults to the USB headset.
Is there any "Ubuntu Way" to do this, or do I have to edit ALSA config files?
I have already tried loading the soundcards kernel module first (worked well on Debian for me), but this machine still sees the headset as default audio device.

---

### Post by jbayone on 2007-03-31
I'd like to know as well, since the same thing happens to me.  Occasionally, and at random, the sound will start to come out of my speakers without changing any kind of settings.

---

### Post by kellemes on 2007-04-01
alsaconf

---

### Post by scotty64 on 2007-04-05
I solved the problem myself by editing /etc/modprobe.d/alsa-base
The trick is to prevent the driver that likes grabbing index 0 (the default device) from doing so and to assign index 0 to the module you would like to have as default.

# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-dummy index=-2
options snd-atiixp-modem index=-2

# Set internal soundcard as index 0
options snd-atiixp index=0

---

