---
title: "Problems with sound quality... (xmms, etc.)"
date: 2006-01-16
forum: Desktop Environments
---

### Post by anb on 2006-01-16
Hello!

I'm quite new to kubuntu, and I already have some problems... The sound quality in XMMS (and some other programs, like Beep Media Player or Stepmania) is quite poor while it's perfect in amaroK...

I did some search on the forums, but I didn't find any solution. I've also installed some codecs and followed the guide about properly configuring sound on [www.ubuntuguide.org](www.ubuntuguide.org). I've also messed with xmms' output plugin options... Nothing helped.

I have an integrated soundcard, nForce2.

What else can I do? Thanks!

---

### Post by anacron on 2006-01-17
i'd check that is amarok and xmms using the same "soundmixer" alsa, oss or esd in this case. You can try change those from the first page in properties, at bottom of page "output plugin", seems like im using oss

maybe this helps something, but i might be wrong too

---

### Post by anb on 2006-01-17
Thanks, but I've already done that and both of them use alsa. I've also tried switching to oss, but the quality was the same... >.>

---

### Post by homersbrain on 2006-01-20
I don't have amarok installed but I have poor sound quality on all my music players (totem, beep etc) when I play any file that isn't using a 48kHz sampling rate (native to the sound card perhaps). DVDs sound just fine for example. 

I am presuming that my linux sound system is incapable of transforming sampling rates properly on the fly and uses a nasty 'snap to' technique instead of oversampling/resampling.

Can anyone illuminate the issue?

---

### Post by TobbeR on 2006-01-24
´Hi
I don't know if you still have sound problems but I had the same problems with xmms while AmaroK's ok. It turned out to be the preamp in xmms which was turned up to high, you find it in the equalizer panel. If this is your problem, lower the amplification or turn of the preamp. 

T

---

### Post by Tiede on 2006-01-24
Also, you might wanna check the PCM volume level. Often the sound volume gets distorted  due to it being to high. Try lowering it to around 70% - 85%. Some Players use the PCM directly to control the volume level, and thus hide the distortion that occurs at a high volume. Others, like XMMS (I think), do not touch the PCM and leave the sound distorted.

---

### Post by StarkD on 2006-02-07
[QUOTE=Tiede]Also, you might wanna check the PCM volume level. Often the sound volume gets distorted  due to it being to high. Try lowering it to around 70% - 85%. Some Players use the PCM directly to control the volume level, and thus hide the distortion that occurs at a high volume. Others, like XMMS (I think), do not touch the PCM and leave the sound distorted.[/QUOTE]

Thanks Tiede! Lowering the PCM volume did the trick for me.

---

