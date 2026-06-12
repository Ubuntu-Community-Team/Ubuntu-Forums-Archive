---
title: "rear-right volume control turns all front speakers but rear-left is OK"
date: 2015-04-12
forum: Desktop Environments
---

### Post by dc740 on 2015-04-12
All channels work fine when I'm listening in VLC (even rear-left speaker!). But the volume control settings for rear-right speaker controls all front speakers (left right and center) and I can't hear anything from the rear-right speaker

I was first having some problems to get 5.1 surround sound working, and here is what I did:
[http://ubuntuforums.org/showthread.php?t=2273289](http://ubuntuforums.org/showthread.php?t=2273289)

Then I added some extra configuration to  "default.pa"
```
$tail -n2 /etc/pulse/default.pa
load-module module-remap-sink sink_name=Surround remix=no master=1 channels=6 master_channel_map=front-left,front-right,rear-left,rear-right,front-center,lfe channel_map=front-left,front-right,rear-left,rear-right,front-center,lfe
set-default-sink Surround
```



Does anyone know what could be the problem? Removing my extra configuration doesn't change anything.

My second problem (and not important compared to the first one) is that I have to add module-remap-sink for the front-center and lfe channels to work. They are muted otherwise.

Thanks in advance

I'm running pulseaudio 4.0 in Ubuntu 14.10 x64. Soundcard: ALC887

---

### Post by dc740 on 2015-04-12
Please move this thread to Multimedia (I didn't know the category existed)

Also, I tried this other setting in default.pa
load-module module-combine slaves=alsa_output.pci-0000_00_14.2.analog-surround-51 channels=6 channel_map=front-left,front-right,rear-left,rear-right,front-center,lfe

And the front-right channel also stops working (the rear-right channel doesn't work correctly either).

---

### Post by dc740 on 2015-04-12
I finally found the problem

My 5.1 reproduces some audio on the front speakers and subwoofer, even when you only send audio to the rear speakers. After a lot of debugging, I found out that there was a broken connector in the rear-right speaker, so I was only hearing the sound from the front speakers. Everything worked just fine after I fixed the connector.

Thanks!

---

