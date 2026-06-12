---
title: "Only 1 application can give sound..."
date: 2006-06-06
forum: Desktop Environments
---

### Post by ZijWePro on 2006-06-06
Hello, it's me again...
I'm experiencing another problem now, and it's the following:
If I play MP3's in XMMS and play a game when XMMS is running and playing music, I don't get sound in that game... I also have the same problem if I'm using TeamSpeak2 (voice communication software) and playing a game.
Can someone help me please? My soundcard is an onboard 5.1 SoundStorm from my nVidia nForce chipset. I've already downloaded the drivers and tried to install them but it says something about the kernel which it can't compile...
Thanks!

---

### Post by ZijWePro on 2006-06-08
*Kick* I wanna have help with this :o

---

### Post by frying_fish on 2006-06-08
Well, you probably have the drivers anyway, but what output are you using, ALSA, OSS, or something else, with ALSA you should be able to have both working together, see what happens if you use the ALSA output for both.

---

### Post by ifokkema on 2006-06-08
[QUOTE=frying_fish]Well, you probably have the drivers anyway, but what output are you using, ALSA, OSS, or something else, with ALSA you should be able to have both working together, see what happens if you use the ALSA output for both.[/QUOTE]

As far as I know, using ALSA or OSS, you get it like this is. No two processes are able to use the soundcard at the same time. To my knowledge, you need to use a sound server (esd) and configure XMMS and such to use the esd to connect to the sound card. See the 'esound' package.

Enable esd:
System -> Preferences -> Sound (sorry, Breezy location)
Check the box 'Enable sound server startup'.

---

### Post by frying_fish on 2006-06-08
well, i use the ALSA output for both xmms and amsn, both can be making sounds at the same time fine on my machine, so thought it should be same on others.  (This was both under slackware with xfce and gnome on ubuntu)

---

### Post by ifokkema on 2006-06-08
[QUOTE=frying_fish]well, i use the ALSA output for both xmms and amsn, both can be making sounds at the same time fine on my machine, so thought it should be same on others.  (This was both under slackware with xfce and gnome on ubuntu)[/QUOTE]

Well, I could easily be misinformed, but I do remember, when using Alsa, that my Evolution sound notifications were silent whenever I had XMMS playing. If I quit XMMS, they started working again. I was then told it was the Alsa setup. Switching to esd has helped me at that time... (Debian Sarge)

---

