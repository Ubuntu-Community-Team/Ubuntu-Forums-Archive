---
title: "DosBox and PulseAudio"
date: 2012-05-08
forum: Emulators
---

### Post by curts on 2012-05-08
I'm having difficulty getting Pro Pinball - Timeshock! audio to fully work in DosBox.  With recent tweaks I made to the DosBox settings using Ubuntu 11.10 I've reached the point where the music track is pretty stable, but the voice and sound effect tracks are silent.  This is still the case after upgrading to 12.04.

Previous forum postings suggest this is a PulseAudio integration issue, but the past recommended fixes are no longer relevant to current Ubuntu releases.

---

### Post by ptrost on 2012-05-09
Make sure you have timidity installed, then edit the dosbox.conf file you're using to specify a midi port of 128:0, then at the console type "export SDL_AUDIODRIVER=oss".

Then when you run DOSBox you will see output like:

DOSBox version 0.74
Copyright 2002-2010 DOSBox Team, published under GNU GPL.
---
CONFIG:Loading primary settings from config file dagger.conf
MIXER:Can't open audio: No available audio device , running in nosound mode.
ALSA:Client initialised [128:0]
MIDI:Opened device:alsa

Midi should work however. I tested with several games and had sound when MT-32 was the card selected in the games' setup.

Can you confirm if that worked for you? If so then add the export to /etc/rc.local so it's set when the system boots.

---

### Post by curts on 2012-05-10
No, that did not work for me.  The midi port was already configured as 128:0.  Setting the suggested environment variable after installing Timidity disabled all sound in the game.  Setting the environment variable to 'alsa' restored the music track.

---

