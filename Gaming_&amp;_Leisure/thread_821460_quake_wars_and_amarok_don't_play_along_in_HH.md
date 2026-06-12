---
title: "quake wars and amarok don't play along in HH"
date: 2008-06-07
forum: Gaming &amp; Leisure
---

### Post by KhaaL on 2008-06-07
I usually listen to music while playing ET:QW - it a neccesity since the game dosen't have any music during the gameplay. Anyway, since I upgraded to HH and with the introduction of pulseaudio I've been banished to play in silence (well, musical silence at least:p). Is there any way to solve this? I thought pulseaudio was supposed to play all kinds of streams wether they were alsa, oss or ESD...

My amarok is configured to use xine engine and Pulseaudio output plugin. I don't know how to check the settings for ET:QW sound settings, if someone knows, let me know too!

---

### Post by KhaaL on 2008-07-07
bumpin...

---

### Post by eragon100 on 2008-07-07
Go to System -> preferences -> Sound

Select ALSA for all the options there.

That fixes the problem, at least for me :wink:

---

### Post by Cappy on 2008-07-07
You could also try starting ET:QW with
```
padsp
```
(PulseAudio OSS Wrapper)

Linux's constant evolution has its good and bad sides.

---

### Post by KhaaL on 2008-07-07
padsp is a poor solution as the sound going through it lags with approx 1 second. Setting the soundoutput to ALSA still won't solve the issue, as i play music in amarok, while its in autodetect mode in the engine tab while starting ET:QW, the game will be silent. If i choose ALSA in amarok, then it will complain that it could not initialize the audio device and hang.

Grr!

---

