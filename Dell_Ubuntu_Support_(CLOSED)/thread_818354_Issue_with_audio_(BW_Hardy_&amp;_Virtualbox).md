---
title: "Issue with audio (B/W Hardy &amp; Virtualbox)"
date: 2008-06-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bmoney80 on 2008-06-04
Hey everyone. So I totally jinxed myself when I previously said everything seemed to be working. I'm now having an issue with audio playback. Basically, after starting Ubuntu, my audio works well. I hear all of the default starting sounds and music playback works through audacious and rhythmbox. 

But ... if I'm playing music through ubuntu while loading xp through virtualbox I have no audio in xp. On the other hand, if I start up my computer and first load virtualbox/xp the sound works perfectly but then the audio wont work in ubuntu. I know this doesnt sound like a huge issue but I need my music to keep me happy as I throw money away to bodog :). 

Okay, so first here is some info:

:~$ aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
--------------------------------------------

:~$ cat /proc/asound/card0/codec#* | grep Codec

Codec: SigmaTel STAC9205
Codec: Conexant ID 2c06
--------------------------------------------

In System>Preferences>Sound...

Soundevents->Autodetect
Music&Movies->Autodetect
AudioConf->Autodetect
Default Mixer Tracks-> HDA Intel (Alsa mixer)

*(After making some other suggested changes - I eventually changed the Default Mixer Tracks to Sigmatel STAC9205 (OSS Mixer) which yielded promising results but did not fix the problem. Prior to this change I was unable to get sound from testing playback if I ran virtualbox/xp first. Upon making this change I was able to run xp with sound and hear the tone while performing playback tests. This still, however, did not fix the problem when trying to play music. 
--------------------------------------------

Okay, so here is what I've done so far to try to fix the issue. 

1. I read in another discussion to change the audio to virtualbox to pulseaudio ->  nothing changed - same exact issue occured. I also tried OSS before and after making other changes but that too did not fix the problem.

2. Following advice in another post, I used the aplay -l and `cat /proc/asound/card0/codec#* | grep Codec' to identify STAC9205 as soundcard/chip and then ...

sudo gedit /etc/modprobe.d/alsa-base

and added ...

options snd-hda-intel model=dell-m44

which was based on information obtained from the same post ...
STAC9205/9254
ref Reference board
dell-m42 Dell (unknown)
dell-m43 Dell Precision
dell-m44 Dell Inspiron (*I have a 1720 Inspiron*)
----------------------------------------------

So, is anyone else having this problem? I'm a complete noob to linux - been running it for about a week so I really have no clue on what to do next and I've been searching the support forum for a couple days now without any luck. 

Any help would be greatly appreciated.

Ben

---

### Post by bmoney80 on 2008-06-04
Well, after messin around a little with some settings it seems that I finally have sound working simultaneously in Ubuntu and Virtualbox/XP. I'm kind of baffled by how it works - so maybe someone can explain this to me?? 

I made the following changes to System>Pref>Sound

Sound Events> ALSA
Music & Movies> ALSA
Audio Conferencing> ALSA
Default Mixer Tracks>Device: Sigmatel STAC9205 (OSS)

And I changed virtualbox audio adapter to ALSA.

Wouldnt the OSS conflict with the ALSA settings? 

B

---

### Post by Toci on 2008-09-26
> **bmoney80 said:**
> Well, after messin around a little with some settings it seems that I finally have sound working simultaneously in Ubuntu and Virtualbox/XP. I'm kind of baffled by how it works - so maybe someone can explain this to me?? 

I made the following changes to System>Pref>Sound

Sound Events> ALSA
Music & Movies> ALSA
Audio Conferencing> ALSA
Default Mixer Tracks>Device: Sigmatel STAC9205 (OSS)

And I changed virtualbox audio adapter to ALSA.

Wouldnt the OSS conflict with the ALSA settings? 

B

 I know this message is not recent but thank you so much!!!, the sound works perfectly and I could even record live streams inside the VirtualBox system.
 As for possible conflicts I didn't notice any but then again the sound I have in Ubuntu is not working fully (which is why I needed VB).

---

