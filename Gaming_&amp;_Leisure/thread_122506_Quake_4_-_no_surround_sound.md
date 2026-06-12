---
title: "Quake 4 - no surround sound"
date: 2006-01-27
forum: Gaming &amp; Leisure
---

### Post by dreamX on 2006-01-27
Hi!
I lately installed the Quake 4 demo and it works almost perfectly. The only thing missing is surround sound. Browsing the archive and the web showed up that entering +set s_alsa_pcm surround51 +set s_numberOfSpeakers 6 is necessary. But it doesn't work.
When turning away from a sound source (like a speaking person) I still hear the this sound in the front. The same when turning to the sound source. It looks like only stereo is working. Choosing "OpenAL" or "Default" makes no difference, "surround" is selected. EAX is not choosable (I think EAX is not available at Linux).
Console output says:



-------- Initializing Sound System ----------
sound system initialized.
---------------------------------------------
--------------- R_InitOpenGL ----------------
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
8/8/8/8 RGBA bits, 24 depth bits, 8 stencil bits
dlopen(libasound.so.2)
asoundlib version: 1.0.9
Alsa is available
------ Alsa Sound Initialization -----
opened Alsa PCM device surround51 for playback
device buffer size: 5461 frames ( 65532 bytes )
allocated a mix buffer of 49152 bytes
--------------------------------------


Any ideas? :confused:

---

### Post by dreamX on 2006-02-02
Really no ideas about that, guys?

---

### Post by veratyr on 2006-02-02
I have the same problem. I have an audigy 2 and 5.1 speakers and still only get stereo. Not really a "major" issue as I only really notice it when characters are talking and you move away from them. Would be nice to be able to hear strogg sneaking up on me though.

---

