---
title: "Are multiple sounds possible on IBM/Lenovo T43?"
date: 2006-02-15
forum: Desktop Environments
---

### Post by StarkD on 2006-02-15
Hi!

I what to start out with that I'm a recent converter from Microsoft Windows and Ubuntu Breezy is working out great for me! I love the freedom, functions, programs, keyboard shortcuts and that Firefox goes much faster.

The only thing I'm not able to fix is multiple sounds on my IBM T43. I've tried "HOWTO: Hear multiple sounds using Both ESD & ALSA" [http://www.ubuntuforums.org/showthread.php?t=32063&highlight=sounds]("http://www.ubuntuforums.org/showthread.php?t=32063&highlight=sounds") without any luck. I've reversed the How To but MPlayer still plays movies with a very strange frame rate.

Anyone else who has it working on a T43?
Any good ideas in general?

---

### Post by queenorych on 2006-02-15
if you are using an alsa driver the dmix plugin will allow you to play multiple sounds.  You may have to configure alsa.  This is the case for any sound card.

The esd will allow multple sounds from all appications using esd.  This is also regardless of sound card.


I would recheck your alsa guide.  Make sure alsa is your preffred sound.  Make sure alsa is defaulting to use the dmix plugin, and not your hardware directly.

---

### Post by StarkD on 2006-02-16
Thanks for the tip queenorych. It was useful to start from.


Now I've learned the following:

My IBM/Lenovo ThinkPad T43 has a Intel ICH6 sound card that doesn't support hardware mixing.

"Ubuntu 5.10 (BreezyBadger) already uses Alsa-base 1.0.9b and has HdaIntel Sound working out of the box." [HdaIntelSoundHowto]("https://wiki.ubuntu.com/HdaIntelSoundHowto")

Running "gstreamer-properties" I choose ALSA as default on output and input.

Which applications that have [ALSA dmix support]("http://www.ubuntuforums.org/showthread.php?t=91127")


The thread above says XMMS and Rythmbox has ALSA support and I can play music at the same time using both. Consequently the problem is in the applications.

Impressing how much you learn at this forum :-D

---

