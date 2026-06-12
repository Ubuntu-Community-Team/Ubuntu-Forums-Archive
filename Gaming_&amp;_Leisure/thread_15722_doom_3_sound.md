---
title: "doom 3 sound"
date: 2005-02-16
forum: Gaming &amp; Leisure
---

### Post by morphodone on 2005-02-16
i just installed doom 3 and everything seems to be working except sound...

sound works for quake 3 and et though and xmms etc

i have a turtle beach santa cruz sound card

any help is greatly appreciated 

thanks

---

### Post by tim1 on 2005-02-16
If you use alsa try

doom3 +set_alsa_pcm pcm

if your standard pcm device is called pcm.

That works for me.

greets, tim

---

### Post by morphodone on 2005-02-16
[QUOTE=tim1]If you use alsa try

doom3 +set_alsa_pcm pcm

if your standard pcm device is called pcm.

That works for me.

greets, tim[/QUOTE]
 hmm, that didn't work
but i eventually got it working
i saw this error

------ OSS Sound Initialization ------
WARNING: failed to open sound device '/dev/dsp1': No such file or directory
WARNING: sound subsystem disabled

i manually edited my DoomConfig.cfg for '/dev/dsp'

thanks

---

