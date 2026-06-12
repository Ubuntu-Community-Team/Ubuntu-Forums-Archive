---
title: "Yet another resolution issue (Xubuntu 9.04)"
date: 2009-06-18
forum: General Help
---

### Post by Chris_Bailey on 2009-06-18
I just finished a fresh install of Xubuntu 9.04 and everything is working masterfully aside from my display resolution and refresh rate. I am hoping for 1368x768 on a 26'' hdtv, and it worked properly using Ubuntu 8.04. I tried getting the restricted drivers for ATI (Ati Radeon 9250) but for some reason they don't pop up in the hardware driver's app. I also installed EnvyNG and tried all available resources from their website. I also setup my Xorg.conf with custom modelines but so far none of that has worked. I do understand that this is a fairly common problem and that I should be able to find the answer by searching but I just haven't been able too. If anyone would like to walk yet another person through this, I would be extremely grateful.

Chris Bailey

---

### Post by s3MA00RRNY on 2009-06-18
When I tried to upgrade to Jaunty on our Mac (Ubuntu GNOME), it said "the restricted driver for your graphics card is not available if you upgrade". You may be having the same problem. ATI must be slow to release updated drivers. My NVidia computer upgraded just fine.

---

### Post by Chris_Bailey on 2009-06-18
Ok after reading all of the problems people have been having with ATI cards, I switched to an older Nvidia card that has worked fine in the past with Ubuntu/Kubuntu. I installed the restricted drivers using the gui tool that comes with Xubuntu and restarted as requested. Now my maximum resolution is 640x480 and I'm really unsure what to do about that. At this resolution my computer is next to unusable, any good ideas?

---

### Post by Yellow Pasque on 2009-06-19
> I tried getting the restricted drivers for ATI (Ati Radeon 9250) but for some reason they don't pop up in the hardware driver's app.
This card hasn't been supported by the proprietary drivers in years (fglrx 8.28 was the last version to do so). In Ubuntu 9.04, only RadeonHD 2x00 and later cards are supported by proprietary drives.

---

### Post by Chris_Bailey on 2009-06-19
Yeah, I was actually wrong about the original card, it was a 9550 (so what). Anyhow, I switched over to an Nvidia Quadro4 XGL 700, which worked fine in the past. Hopefully it's supported. I'm having the same issues with it.

---

