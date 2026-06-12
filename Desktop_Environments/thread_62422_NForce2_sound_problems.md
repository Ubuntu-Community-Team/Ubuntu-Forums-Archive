---
title: "NForce2 sound problems"
date: 2005-09-04
forum: Desktop Environments
---

### Post by Tacit Orange on 2005-09-04
Hello,

I have a Gigabyte GA-7N400 Pro2 Rev 1.x motherboard, which uses the NForce2 chipset. I'm running the Hoary Hedgehog release and have installed nVidia's proprietary NForce driver as per the instructions in [this thread](http://ubuntuforums.org/showthread.php?t=58065). 

My problem is that while I have gotten Xine to play movies, DVDs and mp3s regardless of which sound output I select (OSS, ALSA, etc.), I cannot get either XMMS or BMP to play files of any kind. I have all the GStreamer packages installed and have both of them set to use OSS for output (as the NForce drivers are OSS-only), but I still haven't had any luck in getting them to work. Also, while I can play mp3s in Xine, each new song starts out with stuttering that can only be fixed by hitting "Pause" and then hitting "Play". 

Is there something I'm doing wrong? What do I have to do to get XMMS working?

---

### Post by felipe on 2005-09-04
from what i read:

proprietary nVidia drivers: OSS
ubuntu/linux free drivers: ALSA

i won't go into detail, but OSS has been obsoleted by ALSA since quite some time, why don't you use the default drivers? I have the same HW and use the default drivers

---

### Post by Tacit Orange on 2005-09-04
Oh cool, looks like the default drivers are working now. Thanks!

---

