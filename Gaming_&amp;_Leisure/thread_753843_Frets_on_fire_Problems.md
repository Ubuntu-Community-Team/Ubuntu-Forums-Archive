---
title: "Frets on fire Problems"
date: 2008-04-13
forum: Gaming &amp; Leisure
---

### Post by kinpower on 2008-04-13
Hi, whenever i try to play Frets on Fire nothing happens, so i tried running it through terminal and this came up

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
Traceback (most recent call last):
  File "./FretsOnFire.py", line 64, in <module>
    engine = GameEngine(config)
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 149, in __init__
    self.audio.open(frequency = frequency, bits = bits, stereo = stereo, bufferSize = bufferSize)
  File "/usr/share/games/fretsonfire/game/Audio.py", line 49, in open
    pygame.mixer.init()
pygame.error: No available audio device

Thanks in Advance
Nik :guitar:

Sorry bout the faces but it should be : (                              
(but without the space)

---

### Post by Azzco on 2008-04-16
I think you can disable smileys per post.

Anyways I experience the same issue due to me using oss4.
If you're using alsa you might have a program running with oss.
The old oss drivers doesn't allow software mixing from what I've understood.

The thing that worries me in your messege is the first line Xlib: extension, I have noclue about that myslef.

But make sure that there is no program running with oss hogging your audio device(s). Try to start a music player or something and check if your device is available.

Good luck ;)

---

