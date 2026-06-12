---
title: "Enemy Territory + Skype: Sound problems"
date: 2005-05-13
forum: Gaming &amp; Leisure
---

### Post by arrizaba on 2005-05-13
Is it possible to play [COLOR=Blue]Enemy Territory[/COLOR] while using [COLOR=DeepSkyBlue]Skype[/COLOR]? Does anyone know how to do it?

This is my status:
[COLOR=DarkGreen]ALSA[/COLOR] does not manage to get more than one sound, fine. But [COLOR=DarkOliveGreen]esd[/COLOR] yes. The standard [COLOR=DarkOliveGreen]esd[/COLOR] packed with hoary is not valid to play [COLOR=Blue]ET[/COLOR], so one has to: "killall esd" before playing. The problem is that one is left with [COLOR=DarkGreen]ALSA[/COLOR] and it cannot cope with both sounds from [COLOR=Blue]ET[/COLOR] and [COLOR=DeepSkyBlue]Skype[/COLOR]. 
I tried the proper sound configuration discussed in some forums,  which boils down to installing the [COLOR=DarkGreen]libesd-alsa [/COLOR]package, as described in the [COLOR=Sienna]Ubuntu Guide[/COLOR]:
[FONT=Fixedsys]
[http://www.ubuntuguide.org/#configuresoundproperly](http://www.ubuntuguide.org/#configuresoundproperly)[/FONT]

But, still, if you start [COLOR=DeepSkyBlue]Skype,[/COLOR] then[COLOR=Blue] ET[/COLOR] does freezes at the sound configuration.  ](*,) 
Are there any solutions? Any help would be appreciated.

---

### Post by kolya on 2005-07-11
I am having the same problem and was wondering if anyone knows how to fix it.

---

### Post by Sephiriz on 2005-07-11
I wish I could provide a simple fix here, but instead I'll reference you to two topics that have more thorough instructions on how to allow the your sound configuration to output multiple sound using ALSA and ESD:

**Howto: Happy ALSA, OSS, ESD, with Duplex - Sound Settings**
[http://ubuntuforums.org/showthread.php?t=44753](http://ubuntuforums.org/showthread.php?t=44753)

**HOWTO: Hear multiple sounds using Both ESD & ALSA**
[http://ubuntuforums.org/showthread.php?t=32063](http://ubuntuforums.org/showthread.php?t=32063)

These both helped me greatly, and I was able to run Enemy Territory and XMMS at the same time without any problems using my Sound Blaster Audigy soundcard.  What none of these guides mentioned (I think) was having the sound emulation modules start up with boot, which is covered here:

**Hoary Sound Broke?**
[http://ubuntuforums.org/showthread.php?t=21211&highlight=snd](http://ubuntuforums.org/showthread.php?t=21211&highlight=snd)

If anything, I hope I lead you on the right track.  It sounds to me that you just need to setup ALSA with your own config.  Good luck!

---

