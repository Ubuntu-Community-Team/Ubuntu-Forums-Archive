---
title: "No Sound Skyrim"
date: 2014-07-10
forum: Gaming &amp; Leisure
---

### Post by Luis_Donin on 2014-07-10
Guys I bought skyrim on steam, and I downloaded it, everything is working good, but I have no sound at all and the sound files are missing including the file from the theme song, the only sound I have is the Bethesda sound when I open the game

---

### Post by oldrocker99 on 2014-07-10
From Steam, verify the game cache. This will cause downloads of missing files.

---

### Post by Luis_Donin on 2014-07-10
I've done that 3 times, I doing it again, I downloaded the sound files, but still not working, i've tried installing Dx9 and Dx10, other plugins, I've searched and found out that reinstalling the game won't work either, I'm trying to fix that for since 8am  and everything I try fails

---

### Post by oldrocker99 on 2014-07-11
Did you use the PlayOnLinux script for installing Skyrim with Steam for Windows? It worked very well when I did it, sound and all. In fact, it worked better than the CrossOver script.

---

### Post by Luis_Donin on 2014-07-11
I'm using Play On Linux, I think that this is happening because, first, the files still on the folder "downloading" in the steam directory, and the sound files aren't there

---

### Post by Peter_Solver on 2014-07-12
Do you happen to use Pulseaudio? If so, try to disable it and install alsa-base. Then try to reboot after the switch, see if it works.

---

### Post by Lightning Dragon on 2014-07-15
Hello,

What I did for audio issues was have both Pulseaudio + ALSA, then turn the Windows Version in winecfg to Windows XP mode to get the sound to work. If that doesn't work, disable Pulseaudio as Peter_Solver suggested and use ALSA. Next run DirectX10 from the Skyrim folder itself (do not install through any other way, won't work) and finally, if that doesn't work try installing xact.

However, installing DirextX10 should work if you with Pulseaudio if you change Windows Version to Windows XP. 

Try following the instructions (if the above sounded confusing or something) here:

[http://www.playonlinux.com/en/topic-8864-Elder_Scrolls_V_SkyRim_qNo_sound_device_detectedq.html](http://www.playonlinux.com/en/topic-8864-Elder_Scrolls_V_SkyRim_qNo_sound_device_detectedq.html)
[http://www.steamgamesonlinux.com/skyrim-the-elder-scrolls-v/](http://www.steamgamesonlinux.com/skyrim-the-elder-scrolls-v/) (< how I get Skyrim to work)

---

