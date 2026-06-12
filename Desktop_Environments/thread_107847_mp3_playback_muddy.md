---
title: "mp3 playback muddy"
date: 2005-12-24
forum: Desktop Environments
---

### Post by Nikusan on 2005-12-24
Hi all, 
Recently I've been experiencing problems when playing mp3s. The sound is really bad, muddy, slightly distorted, etc and the bass bottoms out. I'm sure this is not a problem with my hardware or the mp3 files, because if I boot into windows they play fine. This affects all the media players I've tried including totem, rythmbox, vlc, mplayer. So I'm guessing the problem is something lower like the sound daemon, but I've tried switching between ALSA and ESD with no luck.

---

### Post by katu on 2005-12-24
Have you tried xine? Because I also have problems with some mp3s (not all) and xine always plays them ok.  I think it maybe something to do with the bitrate, but I'm not sure... I tried converting to .wav but it still sounded terrible (xine played it ok.)

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-24
It sounds like you have the colume set too high. There's a "bug" (I think they might call it a feature but as an audiophile all I can call it is "bug") where 50% volume on the PCM setting is really "full volume." If you set the slider above 50% then you are making the samples louder than they were on the CD which is bound to cause clipping errors - and nothing sounds bad like "digital clipping."

---

### Post by Nikusan on 2005-12-24
Thanks, &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046;!
I set the PCM down to ~50% and it all sounds fine again.

---

