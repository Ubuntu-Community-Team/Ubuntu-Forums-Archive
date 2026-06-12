---
title: "Frets on Fire won't start"
date: 2008-05-02
forum: Gaming &amp; Leisure
---

### Post by semuren on 2008-05-02
When i try to start Frets on Fire i only get a black flash on the screen and return back to the desktop.

I get these messages from the terminal when I try to start it from the terminal:

ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
Traceback (most recent call last):
  File "./FretsOnFire.py", line 64, in <module>
    engine = GameEngine(config)
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 149, in __init__
    self.audio.open(frequency = frequency, bits = bits, stereo = stereo, bufferSize = bufferSize)
  File "/usr/share/games/fretsonfire/game/Audio.py", line 49, in open
    pygame.mixer.init()
pygame.error: No available audio device
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/apport_python_hook.py", line 78, in apport_excepthook
    report_file = open(pr_filename, 'wt')
IOError: [Errno 13] Permission denied: u'/var/crash/_usr_share_games_fretsonfire_game_FretsOnFire.py.1000.crash'

Original exception was:
Traceback (most recent call last):
  File "./FretsOnFire.py", line 64, in <module>
    engine = GameEngine(config)
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 149, in __init__
    self.audio.open(frequency = frequency, bits = bits, stereo = stereo, bufferSize = bufferSize)
  File "/usr/share/games/fretsonfire/game/Audio.py", line 49, in open
    pygame.mixer.init()
pygame.error: No available audio device


Anyone got an idea on how too fix it? :)

---

### Post by DrStein on 2008-05-04
Hello,

I have the same problem.
I'm sure this is another issue brought to us by Hardy Heron and PulseAudio.

Please, any hints are welcome.

---

### Post by DrStein on 2008-05-05
Okay, you can run it using **pasuspender** as prefix (note that the same applies to other applications).

```
pasuspender fretsonfire
```

Regards.

---

### Post by bartkl on 2008-05-22
Thanks, that works. :) But why?

---

### Post by rodrigo666 on 2008-06-29
Yeah, that worked of me too. But why?

---

### Post by RIchard James13 on 2008-06-29
man pasuspender

>  pasuspender is a tool that can be used to tell a local PulseAudio sound
       server to temporarily suspend access to the  audio  devices,  to  allow
       other  applications  access  them  directly.  pasuspender  will suspend
       access to the audio devices, fork a child process, and when  the  child
       process terminates, resume access again.


So basically it tells pulse audio to get lost and let frets access the sound system directly.

---

