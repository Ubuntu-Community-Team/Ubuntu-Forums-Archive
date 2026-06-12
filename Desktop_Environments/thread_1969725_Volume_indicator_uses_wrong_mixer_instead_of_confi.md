---
title: "Volume indicator uses wrong mixer instead of configured"
date: 2012-04-30
forum: Desktop Environments
---

### Post by kemsky on 2012-04-30
I'm using xfce 4.6.6 (xubuntu 12.04).
PulseAudio fails to restore volume(every boot 100%) of my 5.1 usb headset cm106 ([http://imm.io/nKZK](http://imm.io/nKZK)), 
i decided to switch xfce4-mixer to use ALSA mixer (alsactl and amixer work fine so i could use them to restore last volume) 
see [http://imm.io/nKSr](http://imm.io/nKSr) and [http://imm.io/nKSS](http://imm.io/nKSS).
and  now xfce-volumed(media keys) uses correct mixer(configured ALSA) but  indicator applet still uses different mixer, perhaps pulse.
I've spent a lot of time trying to fix it myself, but now i'm stuck.

---

### Post by LewisTM on 2012-04-30
Yes, the indicator applet uses Pulse only.
Why not uninstall Pulseaudio and use the Xfce mixer panel applet?

If you can't for some reason, create /etc/asound.conf with the following contents then reboot:
```
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
```
This way changes in ALSA volume will be reflected in the indicator sound levels and vice versa.

Cheers!

---

### Post by kemsky on 2012-05-01
Thanks for response.

I have to use pulse to enable audio in my tvtuner via module-loopback, but pulse fails to save/restore volume. I've even tried verbose pulse logs, but there was nothing helpful.

if i create  /etc/asound.conf volume is stiil not restored...

---

### Post by kemsky on 2012-05-01
now its getting worse, after i created  /etc/asound.conf as suggested, minimum volume in alsa mixer is too loud, even if i remove   /etc/asound.conf amd reboot (perhaps it is cached somewhere?). so now i can not control volume without pulse at all.

---

### Post by kemsky on 2012-05-05
anybody?

---

