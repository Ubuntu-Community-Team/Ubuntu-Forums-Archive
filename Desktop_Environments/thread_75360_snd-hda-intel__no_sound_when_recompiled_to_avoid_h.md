---
title: "snd-hda-intel : no sound when recompiled to avoid hotplug boot freeze"
date: 2005-10-13
forum: Desktop Environments
---

### Post by nooky59 on 2005-10-13
Hi,

snd-hda-intel cause hotplug to freeze at boot as stated in the bugzilla :

[http://bugzilla.ubuntu.com/show_bug.cgi?id=15465](http://bugzilla.ubuntu.com/show_bug.cgi?id=15465)

I've tried several methods to get snd-hda-intel working (the prefered one from the Ubuntu WIKI and a manual compilation).

After all the methods, there is no hotplug freeze, the soundcard is detected, I can set it up with alsamixer or the Gnome Sound Applet but no way, there is still no sound...

I've unmutted all the channels (even try to mute them cause I've read that some cards are inverted), put the sound to the max, try both with an headphone but nor from the headphone socket and from the speakers, I manage to get sound.

I'va add this to /etc/modprobe.d/aliases cause it is mandatory in SuSE 9.3 to get sound for example and ind Hoary too if I rember well, but on Breezy, it doesn't do the trick.

alias char-major-116 snd
options snd major=116 cards_limit=1
alias snd-card-0 snd-hda-intel
options snd-hda-intel index=0 id="HDA"
alias char-major-14 soundcore
alias sound-slot-0 snd-card-0
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

Does someone know how to get a soundcard based on snd-hda-intel working on Breezy ?

---

