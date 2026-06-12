---
title: "Mini9 sound missing"
date: 2008-11-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Rallg on 2008-11-01
My mini9 (came with XP, has Ubuntu 8.10 as dual boot) does not play sound on the Ubuntu side. Hardware is OK since XP plays sound. I did not get a webcam, if that makes a difference.

I already searched the forum and found this code:

sudo gedit /etc/modprobe.d/alsa-base

options snd-hda-intel model=dell

But I tried it, rebooted, fiddled with the volume controls and preferences, and still no sound.

Anyone have another idea?

UPDATE: This topic is thoroughly discussed on many threads. The above code is correct. But then, you have to reboot, open the volume control, and make sure that the sound playback volume (not just the master) is properly set. When I fiddled with the volume controls the first time, I failed to fiddle with all of them!

---

