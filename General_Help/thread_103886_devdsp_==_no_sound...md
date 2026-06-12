---
title: "/dev/dsp == no sound.."
date: 2005-12-14
forum: General Help
---

### Post by WetWilly on 2005-12-14
This is the one thing that keeps me from enjoying Ubuntu totally.

The problem is that when I for example listen to music in BEEP Media player using Esound for producing sound I cannot get any sound in applications using the /dev/dsp device... (vmware and teamspeak)

Any idea how I can fix this? Like pointing to another device or anything?

I use the integrated audiochipset on my NForce2 motherboard.

---

### Post by mcduck on 2005-12-15
you could try this: [http://www.ubuntuforums.org/showthread.php?t=30076&highlight=nforce+sound]("http://www.ubuntuforums.org/showthread.php?t=30076&highlight=nforce+sound")

It worked for my Asus A7N8X-E. If it doesn't, search the forum for 'multiple sounds' or something ;)

I think that the other way is to install nVidia's audio driver, it would get your Dolby Digital sound working, but it only uses OSS so you'd loose ALSA and ESD sounds (all system sounds, for example)..

---

