---
title: "No sound after gnome removal"
date: 2005-06-03
forum: Desktop Environments
---

### Post by dejitarob on 2005-06-03
I have an Inspiron 9300 with an Intel ICH6 SigmaTel AC'97. It worked great under Gnome and KDE until I removed Gnome. I tried reinstalling Kubuntu and my sound still does not work in any apps (xmms, amaroK, xine, kaffeine, noatun, realplayer) or system notifications. I attempted the proposed solutions in this [sound thread](http://ubuntuforums.org/showthread.php?t=26567), including muting my external amplifier. I also tried changing the hardware sound system to autodetect, oss, alsa, and esd. Test sound in the Control Center does not work. Output of lsmod | grep snd: ```
snd_intel8x0           32352  1
snd_ac97_codec         74144  1 snd_intel8x0
snd_pcm_oss            52132  0
snd_mixer_oss          19680  1 snd_pcm_oss
snd_pcm                94696  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25060  1 snd_pcm
snd                    55012  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10016  1 snd
snd_page_alloc          9732  2 snd_intel8x0,snd_pcm

``` Output of aplay /usr/share/sounds/KDE_Logout.wav: ```
Playing WAVE '/usr/share/sounds/KDE_Logout.wav' : Signed 16 bit Little Endian, Rate 22050 Hz, Mono

```
Thanks in advanced for anymore suggestions.

---

### Post by dejitarob on 2005-06-04
Still no dice after reinstalling gnome and trying the latest 1.09 alsa drivers. I'm going back to the alsa drivers in the repos. cat /dev/urandom > /dev/dsp does not list the device as busy yet I still cannot hear any sound. This would probably indicate a setting in alsamixer but I tried about every combination I can think of over the past two weeks. I'm just going to go ahead and reinstall Ubuntu then install KDE over it since this is what worked before. I've already wasted too much time on this.

Update: Well I believe I found the culprit. Lately, I have had to play with the headphone plug to sound working working correctly (before this problem). I noticed the headphone looked a bit loose so I tried moving it a bit and it recessed all the way inside the chasis. I looked on Dell's forums and it appears to be a fairly common occurrence. I guess the headphone jack was holding onto the sound and so my speakers were not switching over. Good thing it's still under warranty, supposedly they have to replace the whole motherboard to fix it.

---

