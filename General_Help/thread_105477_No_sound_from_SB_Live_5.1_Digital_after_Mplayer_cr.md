---
title: "No sound from SB Live 5.1 Digital after Mplayer crash"
date: 2005-12-18
forum: General Help
---

### Post by igorilla on 2005-12-18
I used to have a digital output from my SB Live 5.1 Digital card. It was working out of the box and it was still all right in Kubuntu 5.10 Live.

My MpLayer was configured to bypass AC3/DTS sound to the Cambridge Soundworks "receiver". It also had the "Software Mixer" enabled.

My wife touched the volume shuttle and MPlayer got crashed... Immediately the sound was gone. It is only working if DVDs or AVIs with AC3 sound are played.

That was a second time it happened. The first time I had to resort to reinstalling the system and to being very cautious on system updates.

I tried to reinstall ALSA-BASE and ALSA-UTILS and to play with 'alsamixer' and 'alsactl', not to mention KDE and Gnome mixers. No luck so far... The 'Digital link' looks 'Enabled' and all IEC stuff are off, but still...

Any ideas on how to get the sound back without reinstalling?

---

### Post by igorilla on 2005-12-18
This is what happens when you touch the Volume knob in Mplayer and Mplayer is configured for:
* bypass AC3/DTS through SPDIF;
* use Software Mixer;

After that 'kill gmplayer' should be issued (no sudo needed) and all looks clean, but the system is left with no sound (except of DVDs with AC3 sound).

---

### Post by igorilla on 2005-12-18
The system wide sound misteriously returned back on!!!

After numerous tricks, I returned everything back to how it was and did the following:
* stopped 'alsa-utils', 'alsa';
* deleted '/var/lib/alsa/asound.state'; '/var/run/alsa/modules-removed' and '/var/lib/gstreamer/0.8/';
* restarted alsas and still no luck...
* desperately rebooted PC and then made it through KMix!!!!

The bottom line: DONT USE Software Mixer ON DVD PLAYBACK!!!

---

### Post by el_pombo on 2006-07-25
I had a similar problem with my Sound Blaster Live 5.1 Digital, I couldn't hear sounds from the card's digital out even after rebooting the system (currently Dapper Drake, but it also happened with Breezy Badger). This happened more than once, always after using totem or xine with AC3-PASSTHROUGH enabled. I'm not sure if the player crashed everytime the problem occured. Anyway, I was able to solve this by recompiling the alsa drivers. If anyone happens to have this problem and rebooting doesn't work, follow this guide: [http://ubuntuforums.org/showthread.php?t=205449&highlight=dpkg-reconfigure+alsa-base]("http://ubuntuforums.org/showthread.php?t=205449&highlight=dpkg-reconfigure+alsa-base") to recompile or, probably, just reinstall alsa to get the sound working again.

Good luck.

---

