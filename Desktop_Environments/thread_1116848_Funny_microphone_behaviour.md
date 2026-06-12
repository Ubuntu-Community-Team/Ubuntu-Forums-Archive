---
title: "Funny microphone behaviour"
date: 2009-04-05
forum: Desktop Environments
---

### Post by deflagrator on 2009-04-05
I am running Ubuntu 8.04.2. I cannot get my microphone to work
properly though.  When I have it plugged in and tap it with my finger,
I can hear that on my speakers. When I blow gently into my microphone,
I can hear that too on my speakers. However, no speech gets amplified
unless I get so close to the mic that it is virtually in my mouth.

What is ridiculous is that this behaviour occurs irrespective of what
the volume settings are. i.e. whether the Master, PCM, Front, Front
Mic are turned on or off. In fact, I get the above sounds (tapping,
blowing and talking really close to the mic) from my speakers even when
they are muted!

I am running the Alsa mixer. I haven't been able to figure out what's
going on. Someone please throw light. I want to use my mic for
recording sound into wav files using Audacity, and for using Skype.
These haven't been possible yet.

dsv

P.S. I have this problem with two microphones, both of which work fine on Windows XP. So I know that my microphone is not the problem.

---

### Post by Giblet5 on 2009-04-05
Sound card manufacturers don't (usually) provide software for Linux and they're often stingy about technical details.

It's a miracle that sound works as well as it does under Linux. That said, I have three of the most complicated sound cards available, and all three work perfectly - even the 16-channel mixer card.

You probably need to tweak Alsa's idea of which input is really the Mic, since it's clear that Alsa has that (and probably other settings) confused.

The [Alsa forums]("http://ubuntuforums.org/tags.php?tag=alsa") are your best bet.

Repost there and at least tell them what hardware you have (sound chip manufacturer, model, etc).

---

### Post by corpsehacker on 2009-04-05
It could be the Mic. I have 2 microphones, one really old one and one new one, and the old one fails to work but the new one works fine. On the other hand, as the other guy has already stated, it could be the sound card, my sound card has no drivers for ubuntu, that is why I am stuck using motherboard sound and microphone. At any rate good luck.;)

---

### Post by deflagrator on 2009-04-05
I have reposted this question under Multimedia and Video. I have a sound card that came with my Intel D945GCPE mother board. FYI, only my mic is having issues. My speakers play okay, and I can play CDs, DVDs, VCDs etc. just fine. So the sound card maker needs to have been selectively stingy.

Btw, corpsehacker, could you elaborate a bit on what you mean when you say that you are using your motherboard sound and microphone?

dsv

---

