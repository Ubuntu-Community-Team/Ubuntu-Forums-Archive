---
title: "Need to fix /dev/dsp"
date: 2005-05-29
forum: Desktop Environments
---

### Post by &#12465;&#12452;&#12488; on 2005-05-29
I bet this is really easy to solve, but anyway. OSS playback haven't worked for a while, and since not all applications support ALSA, I thought I'd take a closer look to find out what's wrong.

Then I discovered that /dev/dsp and /dev/audio were replaced with some wav-file. So all I have to do is create some new symlinks and stuff them in /dev, or something like that anyway, right?

I may know the problem, but I'm unsure how to solve it. How will I know what to link, and HOW do I link it? It's not very important, but I'd like to have OSS working too.

---

### Post by cwaldbieser on 2005-05-29
I believe there is a script called /dev/MAKEDEV you can use to create missing device nodes.
```

$ man MAKEDEV
```
should give you the relevant details.

---

### Post by Martin Witte on 2005-05-29
I always thought the sound issues were the most hard part to solve in Linuix, so Ubuntu has been a relevation in fixing it (where e.g. Debian and Suse fail for me). please add more specific information - like where(websites, cds, etc), what(totem, mplayerl etc) and how (cds, dvds, mp3s,, etc) you have issues with sound.

---

### Post by &#12465;&#12452;&#12488; on 2005-06-18
I tried to do **MAKEDEV audio** some time ago after reading the manual, but it didn't work. Today, I tried to do **MAKEDEV -d audio**, and then **MAKEDEV audio** afterwards. Now OSS seems to be working again, but the playback sounds very fuzzy. At least it's better than nothing.

---

### Post by foo on 2005-06-18
Try:

# modprobe snd_pcm_oss

---

