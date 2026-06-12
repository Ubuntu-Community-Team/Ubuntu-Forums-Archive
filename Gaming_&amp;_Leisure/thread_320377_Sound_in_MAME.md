---
title: "Sound in MAME"
date: 2006-12-17
forum: Gaming &amp; Leisure
---

### Post by cneil on 2006-12-17
Hello,
I really like being able to run MAME and play music using VLC at the same time.  However, whenever I try to turn off the sound in MAME, the sound to my entire system stops working.  Currently, it is possible to play video game music and audio files at the same time, but I can't turn off the video game sound and continue playing audio files. Is it possible for me to disable sound in MAME and run other audio applications at the same time?
Thanks

Note- I am running Dapper Drake sing an ATI ISP Alsa Mixer.

---

### Post by cneil on 2006-12-19
Bump, there has to be a workaround for this.

---

### Post by gedge on 2009-01-10
It looks like the [-nosound] switch is not available in the ubuntu compile of xmame.  I've been able to get around this by setting the audio device to [/dev/null].

    xmame -audiodevice /dev/null <path/to/rom>

With this done- I can use mpg123, or amarok etc... to listen to audio while playing games in xmame.

---

### Post by disturbedite on 2009-01-12
upgrade to sdlmame, it is actually actively developed. xmame has been dead for years.

see if that fixes your problem.

if not, i'm not exactly sure how to fix the problem, but it looks like it is adjusting system volume and not software (the individual program's) volume. look for an option to switch the volume control to software.

the audio player audacious has this exact option, as does other media players.

---

