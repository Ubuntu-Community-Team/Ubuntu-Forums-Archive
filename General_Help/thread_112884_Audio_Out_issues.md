---
title: "Audio Out issues"
date: 2006-01-05
forum: General Help
---

### Post by winter_mute on 2006-01-05
I've been having a problem that's being very difficult to solve, and that is one of audio out.  No matter which driver I use, there's always this... I suppose the best way to describe it is 'tinny' sound.  I know it's not the audio file, and I know it's not the mobo or the built in audio jacks, because they both work just fine when I'm running XP.  And it's just getting kinda annoying.  I've tried all the drivers, all the combos I can think of... but to no avail.  Any help here?

The only problem with this is that if I play around with the drivers, they'll eventually get rid of the sound issues.  But I've kept notes as to which drivers have done this each time, and it's never been the same each time.  I'm just so freaking confused.

---

### Post by winter_mute on 2006-01-06
Any help?  Please?  I'm really suck on this.

---

### Post by 23meg on 2006-01-06
What's your sound card? Does this happen with all sound systems (ALSA, OSS etc.)?

---

### Post by winter_mute on 2006-01-14
My soundcard is whatever's built into my mobo.  As far as I can tell, that would happen to be a ADI AD1980 SoundMAX 6-channel CODEC.  asound -l gives me "**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 0/1
  Subdevice #0: subdevice #0"

Now I'm just getting an issue of no sound at all on occasion, where nothing can construct a pipeline.  Which, as far as I know, shouldn't happen since I havn't changed anything.

---

