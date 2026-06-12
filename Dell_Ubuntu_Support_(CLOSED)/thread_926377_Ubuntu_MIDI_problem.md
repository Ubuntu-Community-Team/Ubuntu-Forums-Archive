---
title: "Ubuntu MIDI problem"
date: 2008-09-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by zonination on 2008-09-21
Good evening, gentlemen!

I recently tried to construct some sheet music with Rosegarden, and, while Ubuntu doesn't seem to have a problem with the MIDI format during playback, it also doesn't seem to be playing anything at all. Yes, the volume is at max and it works with other formats other than MIDI.

I currently have the ALSA driver installed, as well as mplayer (not sure if the latter will accomplish anything). I believe my sound card is ATI, but I'll need to check on that.

Is there any way I can get MIDI to play?

Thanks in advance!
~Zoni

---

### Post by luctor on 2008-09-22
Rosegarden should be playing the Timidity Soft Synth out of the box.
Check the midi outputs in Rosegarden if it finds the softsynth.

Maybe these resources can help you with your setup.
[https://help.ubuntu.com/community/Midi/HardwareSynthesisSetup](https://help.ubuntu.com/community/Midi/HardwareSynthesisSetup)
[https://help.ubuntu.com/community/Midi/SoftwareSynthesisHowTo](https://help.ubuntu.com/community/Midi/SoftwareSynthesisHowTo)

You might also want to run a realtime kernel


For me playing MIDI works at random. Sometimes I can hear sound, sometimes not. For me personally not a big deal because I usually have my Yamaha Keyboard (PSR-295) connected, so I use that one for sound.

Rob 
 


Rob

---

