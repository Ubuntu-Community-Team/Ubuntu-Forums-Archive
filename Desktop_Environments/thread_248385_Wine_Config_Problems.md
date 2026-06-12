---
title: "Wine Config Problems"
date: 2006-09-01
forum: Desktop Environments
---

### Post by handband2 on 2006-09-01
I'm wondering if anyone else is having the same problems configuring wine as I am?

I just installed wine (0.9.20):  [https://help.ubuntu.com/community/BuildingWineFromSource](https://help.ubuntu.com/community/BuildingWineFromSource)

Everything appears to run fine but when I go into "Wine configuration" (winecfg).  I can't click on the "Audio" tab without it crashing and giving me this error:

```
fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)
ALSA lib pcm_dmix.c:762:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dmix.c:762:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Creating link /home/ubuntu/.kde/socket-ubuntu.
can't create mcop directory

```

I hope someone can help me solve this problem.

Thanks!!

---

### Post by shirilover on 2006-09-01
try doing
mkdir /home/ubuntu/.kde/socket-ubuntu

---

### Post by handband2 on 2006-09-02
I doubt that would fix the problem.  I'm thinking the error is coming from the OSS or/and ALSA driver.

---

### Post by DougieFresh4U on 2006-09-02
I get the same mesasge some times. I am having great many problems installing. I had it installed then when I went to open thegame using wine I got ' No Active X Control' and I cannot seem to get Active X installed](*,)

---

### Post by CatKiller on 2006-09-02
> **handband2 said:**
> Everything appears to run fine but when I go into "Wine configuration" (winecfg).  I can't click on the "Audio" tab without it crashing and giving me this error:

```
fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)
ALSA lib pcm_dmix.c:762:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dmix.c:762:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Creating link /home/ubuntu/.kde/socket-ubuntu.
can't create mcop directory

```

I hope someone can help me solve this problem.

Thanks!!It sounds to me like Wine thinks it should be using both OSS and ALSA at the same time. Which the documentation suggests would be a Bad Thing. Of course, if it crashes whenever you go to the Audio tab, then it's quite hard to turn one of them off.

If you type ```
wine regedit
``` into a terminal you might be able to change the HKCU/Software/Wine/Drivers/Audio key to alsa. Of course, it might be something else. I believe that most of the Wine configuration info is mirrored in the pretend Windows Registry, so have a look around if you can't get winecfg to work.

---

### Post by handband2 on 2006-09-02
I looked under ```
HKCU/Software/Wine/Drivers/Audio
```

My registery doesn't have "Audio".  Here is what I have:
```
HKEY_Current_USER
     + Control Panel
     - Software
       + Microsoft
       - Wine
           Debug
           Direct3D
         + Fonts
           MSHTML
           Temporary System Parameters
```
This might be the problem?  

Maybe it can be manually created?  

Can anyone share the settings of thier "Audio" key?

Thanks!

---

### Post by CatKiller on 2006-09-04
> **handband2 said:**
> This might be the problem? Maybe. I noticed you didn't have a DirectSound, either.
> Maybe it can be manually created?Maybe. I have no idea really, but it's only a text file, so I can't think of any reason not to try.
> Can anyone share the settings of thier "Audio" key?
This is from my ~/.wine/user.reg file:
```
[Software\\Wine\\DirectSound] 1157180247
"DefaultBitsPerSample"="8"
"DefaultSampleRate"="22050"
"EmulDriver"="Y"
"HardwareAcceleration"="Standard"

[Software\\Wine\\Drivers] 1157180368
"Audio"="alsa"
```I don't know what the numbers mean. Just paste it in between the Direct3D bit and the Fonts bit. Chances are, it won't work and it's something else that's broken, but it's got to be worth a try.

---

