---
title: "How to show old mixer panel Ubuntu 9.10"
date: 2009-10-03
forum: Desktop Environments
---

### Post by tolostoi on 2009-10-03
In Karmic there is a new interface for volume control and mixer (indeed in debian sid too, maybe from newest gnome :) ) I hate pulse audio, till now I succeed to combined pulse with alsa to work fine toghether on my system. Sound in karmic is terrible, I remove the pulse audio, seems everything works fine (even system sounds) but this ((see screenshot)
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=130571&d=1254566675[/IMG]
is gone :( I remember when the new mixer come in debian, I google it and find a command that show the old panel, but forgot it :(, maybe something starts with gstreamer or alsa_something, Please help with this command :P
```
01:08.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)uname -a
Linux foo 2.6.31-11-generic #38-Ubuntu SMP Fri Oct 2 11:55:55 UTC 2009 i686 GNU/Linux
```

Before removing the pulseaudio only smplayer (mplayer) work fine with alsa output and with crystal sound, without defects. Work fine with stereo and 5.1 output (just magic app is mplayer :))

Edit: I'm not alone [https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/440465](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/440465)

---

### Post by photonik on 2009-11-15
> **tolostoi said:**
> 
is gone :( I remember when the new mixer come in debian, I google it and find a command that show the old panel, but forgot it :(, maybe something starts with gstreamer or alsa_something, Please help with this command :P


I've just faced the problem with sound in Karmic.  The command that you needed to show the sound mixer from terminal is:  "alsamixer -Dhw"

Goodluck!

---

