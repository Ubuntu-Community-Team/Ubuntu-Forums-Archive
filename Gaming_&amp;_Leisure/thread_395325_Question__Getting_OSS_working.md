---
title: "Question:  Getting OSS working"
date: 2007-03-28
forum: Gaming &amp; Leisure
---

### Post by sticks on 2007-03-28
I have an old copy of Descent3 Linux that I want to play in
Ubuntu edgy, but the readme says oss compatible audio is 
needed.  i installed alsa-oss though Synaptic but when I try 
to set the sound driver preferences to oss no sound comes
out when I'm testing it,  and I get no sound or music from
the game. 
The sound hardware that's in my Compaq laptop is Conexant
integrated ac link audio.  I don't know if I don't have a proper 
driver setup or if the audio chipset doesn't support this.
Does anyone here have any hints to get oss audio capability 
working properly in integrated audio hardware?

---

### Post by Monk-e on 2007-03-28
I must say I don't know much about this topic. but maybe check if the game is using the right device? I've had times when my OSS device was /dev/dsp and then other times when it was /dev/dsp1.

---

### Post by sticks on 2007-03-28
> **Monk-e said:**
> I must say I don't know much about this topic. but maybe check if the game is using the right device? I've had times when my OSS device was /dev/dsp and then other times when it was /dev/dsp1.


The only configuration settings I could find for this game was file
".Descent3Registry" and there is no mention of a sound device in 
this file.       I installed Quake3 and had sound work perfectly so I
don't know why sound wouldn't work in Descent3 except for the
the fact that it depends on oss audio which doesn't work for me.

---

### Post by sticks on 2007-03-29
Is there no way to get oss/mmap dependent game applications
to run in Ubuntu?
I just spent the  entire afternoon trying steps listed here
[http://www.sabi.co.uk/Notes/linuxSoundALSA.html#emul](http://www.sabi.co.uk/Notes/linuxSoundALSA.html#emul)
and still nothing

---

