---
title: "Vostro 220 Sound"
date: 2009-01-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dnowell on 2009-01-19
I've got a Vostro 220 that I've been trying to get sound working on for a couple weeks now.  This is intended to get my parents off Windows, but if I can't get audio it'll probably be a hard sell....I'm running 8.04, although I've also tried 8.10 & 7.10.  Neither works any better.

I've followed the suggestions in this message and installed alsa-1.0.19
[http://ubuntuforums.org/showthread.php?t=1017575](http://ubuntuforums.org/showthread.php?t=1017575)

No luck.  If I set the Sound Playback device in Preferences - Sound to ATI HDMI it will run the test without any errors, but I still don't get sound.  Has anyone else been able to get sound working on one of these?  I'm real close to going out and buying a used sound card just to get something that might be supported.

~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC662 rev1

---

### Post by williemach on 2009-01-30
Hey there,

I read your post and realized you are having problems with sound on the 220. Please check out my post again, i've updated with a few things. I also clarified which file needs to be modified to load the appropriate driver.

According to your post, it looks like you do indeed have the codec, but you need the modprobe file to know about it. Load the driver into /etc/modprobe.d/alsa-base by doing the following:

1. Sudo vim /etc/modprobe.d/alsa-base
2. At the bottom of the file enter in options snd-hda-intel model=3stack-6ch-dig

---

