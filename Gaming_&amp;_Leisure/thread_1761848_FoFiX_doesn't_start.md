---
title: "FoFiX doesn't start"
date: 2011-05-18
forum: Gaming &amp; Leisure
---

### Post by ssj71 on 2011-05-18
I just installed FoFiX on Natty from the ubuntu software manager. I tried starting it up and it opens a black python window titled FoFiX, rails the CPU, and does nothing. I couldn't even kill it except by restarting. I looked in the log and it listed no errors. I tried in a terminal and it did the same thing. It had some ALSA_pcm errors such as could not find device or create slave or something, and bluetooth stuff like could not connect, then it says jack server could not be found or started.

I rebooted again and started jack and tried again with identical results (black window that I can't kill) except without the jack server error.

Any ideas? Thanks.

---

### Post by ssj71 on 2011-05-18
Here's the output from the terminal:
```

~$ fofix 
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started


```

Here's the fofix log:
```

[    0.000772] (D) Logging initialized: Wed May 18 16:33:57 2011
[    2.015074] (W) Pitch bending is not supported; install john.stumpo's pitchbend module (r7 or higher) if you want it.
[    3.908379] (D) GameEngine class init (GameEngine.py)...
[    3.908422] (D) FoFiX v3.121 Final starting up...
[    3.908439] (D) pygame version: 1.9.1release
[    3.908762] (D) Initializing audio.
[    3.944566] (D) Audio configuration: (44100, -16, 2)
[    4.023783] (D) Initializing pygame.mixer & audio system at 44100 Hz.
[    4.023866] (D) Initializing video.
[    4.120461] (W) Video setup failed. Trying without antialiasing.
[    4.341958] (D) Compiling shader "stage" from ../data/shaders/lightning.vert and ../data/shaders/lightning.frag.

```

---

### Post by ssj71 on 2011-05-20
And if it makes any difference I installed Frets on Fire and it works fine.

---

### Post by R33D3M33R on 2011-05-26
Try editing the video section in ~/.fofix/fofix.ini

Set: shader_use = False
And: multisamples = 0

---

### Post by higashi on 2011-12-23
I'm having the same problem.
After installing from the software centre, I opened it and got a blank window. I looked for my fofix.ini folder to edit it as R33D3M33R suggested, but that folder didn't seem to exist.

Out of desperation, I tried uninstalling it and then reinstalling via the terminal (using [these]("http://fretsonfire.wikidot.com/fofix-install") instructions) but that didn't work at all (i couldn't find the game anywhere after it was supposedly done installing)

---

### Post by R33D3M33R on 2011-12-23
I have attached the ini file for my game. Rename it from fofix.txt to fofix.ini and put it in the ~/.fofix/ folder.


You should try the repository version first.

---

