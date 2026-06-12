---
title: "How to rescan for HDMI sound"
date: 2020-06-22
forum: Desktop Environments
---

### Post by irober02 on 2020-06-22
If I resume my suspended Ubuntu 20.04 desktop before I power up the attached HDMI monitor the HDMI sound output device is absent.

The only way I can fix the situation is to reboot the system (with the monitor on).

If I take care to power on the HDMI monitor FIRST and then wake up the computer all is OK.

I presume there is a way to get the system to re-scan for audio devices short of a reboot but my experiments and searches have been fruitless.

Can someone please enlighten me?

regards

ian

---

### Post by CatKiller on 2020-06-23
One thing you could do is set your HDMI output as the default ("fallback") output. That would make all audio streams get moved to that output as soon as it appears. That's just drag-and-drop in KDE, but I understand that Gnome's audio options are quite limited by default.

Another option is to use ```
pulseaudio -k
``` to kill PulseAudio, which will then restart. The kill/restart cycle takes a couple of seconds on my hardware.

---

### Post by irober02 on 2020-07-03
Thanks for the suggestion but that doesn't work for me.

---

