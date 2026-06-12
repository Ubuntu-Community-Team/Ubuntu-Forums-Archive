---
title: "ScummVM and sound?"
date: 2006-02-01
forum: Gaming &amp; Leisure
---

### Post by Poldi on 2006-02-01
hi all.

I have installed ScummVM and the 2 adventures that come with Breezy from Universe and can play them just fine.

but only in silence... how do I enable sound?

the sound options in ScummVM default to 'default' - I hear nothing. when I change them to 'ALSA' ScummVM crashes when I start a game. 

I have tried changing my Gnome-desktop multimedia settings from 'ESD'[default] to 'ALSA' but this has changed nothing. ScummVM still crashes starting a game. I would like to fiddle as little as possible with my overall Ubuntu sound settings because everything else is working just fine multimedia-wise.

any help?

kind regards,
Carsten

---

### Post by LordBug on 2006-02-28
If you already solved this, then ignore.  I finally managed to get sound and music working in SCUMMVM.  It took some digging to get the info.

This all assumes you have SCUMMVM installed from Synaptic (currently 0.7.1).

1) Pop into Synaptic and install libsdl-alsa.  This will delete libsdl-oss.  I don't want OSS, so I don't care.  This will allow you to use "ALSA" in ScummVM.

2) Midi music.  This is a tricky one.  You'll need to read:
[utl=https://wiki.ubuntu.com/MidiSoftwareSynthesisHowTo]This one for software MIDI synthesis[/url]
[This one for hardware MIDI synthesis](http://ubuntuforums.org/showthread.php?t=30963)

3) Set ScummVM audio to "Default".

Following these (hardware MIDI for me) got me sound effects and full music in Beneath a Steel Sky.  I have yet to try with other games.

---

