---
title: "Remove OSS in favor of ALSA"
date: 2004-12-12
forum: Desktop Environments
---

### Post by Arbiter on 2004-12-12
Hi all,

I know that Ubuntu uses both OSS and ALSA at the same time, but I was wondering if it was possible to totally remove one in favor of the other.  I want to disable OSS and let ALSA take over sound duties for all programs and such.  How do I stop OSS from loading?

Any help would be appreciated.

---

### Post by Arbiter on 2004-12-13
Anybody?

---

### Post by gfg on 2004-12-13
I would like that too. The sound sounds better in Alsa.

---

### Post by ploum on 2004-12-13
To really disable OSS, you need to recompile your kernel.

I personnaly suggest that Ubuntu ship kernel without OSS by default in the future. With the OSS layer of ALSA, there's no need of keeping native OSS and this is the cause of many sound failure. (Half of warty I've seen installed don't have sound by default because there's a conflict between OSS and ALSA)

---

### Post by Arbiter on 2004-12-14
[QUOTE=ploum]To really disable OSS, you need to recompile your kernel.

I personnaly suggest that Ubuntu ship kernel without OSS by default in the future. With the OSS layer of ALSA, there's no need of keeping native OSS and this is the cause of many sound failure. (Half of warty I've seen installed don't have sound by default because there's a conflict between OSS and ALSA)[/QUOTE]


Exactly.  I'm getting buggy sound on my laptop because of Ubuntu's split personality when it comes to a sound server.  I hope someone on the devel team is listening to this one...

Sound plays for me, but it's got a few flaws because of the conflict.  I can only play one sound at a time, and when I try and use ALSA with XMMS, it plays but there are gaps in the sound every so often with my MP3 and OGG files - I mean, they play, but every minute or so it seems like ALSA has to catch up with itself or something and there is a gap in the audio.  I use my laptop to DJ a radio show at my college and I can't have problematic audio like this...

Don't get me wrong, I love Ubuntu - its definitely more innovative then Fedora Core in many aspects, but I may be forced to return to it until a future release of Ubuntu handles sound better.

Sorry...just venting  :D

---

### Post by eeried on 2006-10-09
It seems OSS is still in the kernel (Xubuntu Dapper)
/lib/modules/2.6.15-23-386/kernel/sound/oss

Is that so?

---

### Post by alphanimal on 2007-08-13
Hey, I have definitely the problems with ALSA / OSS...
Here's the Thread with the details (no answers so far):
[http://ubuntuforums.org/showthread.php?t=524877](http://ubuntuforums.org/showthread.php?t=524877)

Are you serious there's no way of disabling OSS without re-building the kernel?

And it this is so, how do I rebuild the kernel? is it much work?
(I'm quite new to Linux at all)

and if i cannot rem ove OSS at all can i prevent it from stealing control over a specific sound card?

thx

---

### Post by janfsd on 2007-08-25
Don't remove OSS, it's portable (alsa is linux only), well documented, it is much easier for developers to work with, now it is gpled and several other things, read this: 

[http://4front-tech.com/hannublog/?p=5](http://4front-tech.com/hannublog/?p=5)

Instead try implementing the newer oss version that has been released and it is gpled, btw the old version that is included is like 10 years old! That's why it lacks several futures. All this is in the link, I recommend the reading.

---

