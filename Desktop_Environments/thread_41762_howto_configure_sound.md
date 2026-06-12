---
title: "howto configure sound?"
date: 2005-06-14
forum: Desktop Environments
---

### Post by brutus on 2005-06-14
When I play movie, there is no sound. Gstreamer is set to Alsa but I checked all. I use xine but other players (totem, vlc ) works like xine. I see picture without sound. Xine is set to alsa. Sound test failed but xmms plays mp3 files very good. 
I have 2 soundcards: onboard Via... and  c-media cmi8738 ( I use this one).
How can I set this sound?

---

### Post by sethmahoney on 2005-06-14
If you have it set to use ALSA, typing

```
killall esd
```

at the terminal before launching the video player should make sound work.  For a more permanent fix, there is a HOWTO for getting sound to work exclusively through ALSA.  A quick search should pull it up.

---

### Post by wowbagger999 on 2005-06-14
Instead of killing esd, try this:
 
edit File: /etc/esound/esd.conf

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100


credits to [http://gentoo-wiki.com/HOWTO_ALSA_sound_mixer_aka_dmix#esound](http://gentoo-wiki.com/HOWTO_ALSA_sound_mixer_aka_dmix#esound)

worked for me


best regards

walter

---

### Post by afonic on 2005-06-14
[QUOTE=brutus]When I play movie, there is no sound. Gstreamer is set to Alsa but I checked all. I use xine but other players (totem, vlc ) works like xine. I see picture without sound. Xine is set to alsa. Sound test failed but xmms plays mp3 files very good. 
I have 2 soundcards: onboard Via... and  c-media cmi8738 ( I use this one).
How can I set this sound?[/QUOTE]
 This thread is all you need:

[http://www.ubuntuforums.org/showthread.php?t=26567](http://www.ubuntuforums.org/showthread.php?t=26567)

Do some search before you post! :-)

---

