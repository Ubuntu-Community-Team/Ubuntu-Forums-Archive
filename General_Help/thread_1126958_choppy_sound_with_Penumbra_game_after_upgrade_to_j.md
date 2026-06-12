---
title: "choppy sound with Penumbra game after upgrade to jaunty..."
date: 2009-04-15
forum: General Help
---

### Post by hardyn on 2009-04-15
Everything worked well under 8.10, although now i am getting very choppy very slow audio with 9.10; it is slightly affecting video frame rate as well.

the audio works well on everything else.  music plays, videos have audio, system sounds are fine.

as far as i can tell its only the penumbra game (which i bought so i would like to get this working) that i am having this trouble with.

i played with all the mixer settings and changed all sound handlers to alsa, and after about 30 seconds of the choppy glitchy audio it cleaned up and was clear... this is not consistent however, sometimes audio is fine, most of the time its not.

I would rather not uninstall pulse, but is there any alternative?  are there any major pulse upgrades coming down the pipe before release?


Thanks for any help.

---

### Post by paradigm2 on 2009-04-16
> **hardyn said:**
> Everything worked well under 8.10, although now i am getting very choppy very slow audio with 9.10; it is slightly affecting video frame rate as well.

the audio works well on everything else.  music plays, videos have audio, system sounds are fine.

as far as i can tell its only the penumbra game (which i bought so i would like to get this working) that i am having this trouble with.

i played with all the mixer settings and changed all sound handlers to alsa, and after about 30 seconds of the choppy glitchy audio it cleaned up and was clear... this is not consistent however, sometimes audio is fine, most of the time its not.

I would rather not uninstall pulse, but is there any alternative?  are there any major pulse upgrades coming down the pipe before release?


Thanks for any help.

Negative.  My understanding is that Pulse-Audio will not be updated in Jaunty anymore past the freeze.

However PulseAudio just released a new version and I upgraded it myself through unofficial channels using a PPA:

[http://ubuntuforums.org/showthread.php?t=1126128](http://ubuntuforums.org/showthread.php?t=1126128)

Doing so is at your own risk.  It might fix your issue.

---

### Post by hardyn on 2009-04-16
Thanks, i will give that a whirl later tonight.

---

### Post by hardyn on 2009-04-16
> **hardyn said:**
> Thanks, i will give that a whirl later tonight.

Hey, Cool... it works.

Thanks.

---

