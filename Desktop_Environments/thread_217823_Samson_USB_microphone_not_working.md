---
title: "Samson USB microphone not working"
date: 2006-07-17
forum: Desktop Environments
---

### Post by khaledaboualfa on 2006-07-17
I'm trying to use my Samson USB mic. For some reason I can't seem to get it to work however. Usin Alsa Mixer if I go to change device, it does bring it up, so it's recognising the thing, however for some reason it's just not working if I use Sound Recorder or Audiocity. No signal back to the actual microphone at all. Any ideas what settings I've got to put in to make it work?

Do I need to keep switching between my sound card and the mic? Is there a tutorial for me to just have the mic operating as a mic and the soundcard as the general output?

---

### Post by quicktime1 on 2006-08-07
I have this same problem as you. I also have a Samson USB Mic, and as far as Ive tried I have yet to get it to work. It recognizes it right but as you said, no sound goes into the computer. Im hoping that in the future this could be worked out, specially with Ubuntu Studio starting to catch steam. According to the people at Samson, it works on Linux, but there's absolutely no support for it. Oh well, we will have to wait I guess.

---

### Post by johndian on 2007-06-05
I got Samson mike to work beautifully in audacity by going to edit, preferences, and changing default recording device to  Alsa Samson C01U.
Hope this helps

---

### Post by BCtom on 2008-04-15
I just purchased a Samson C01U because I needed the good bottom end on vocals, and I too had it working with no problems in Audacity. The only real change that I made that seems to cut a lot of headaches (besides going through shell) was setting the system sound mixer to: 
[INDENT]_1_.Samson C01U (Alsa mixer)
[/INDENT]as the default. 

Double click on the speaker (Volume Control) at the upper right-hand corner of the Desktop and choose File --> Change Device --> _1_: Samson C10U.... If your system is detecting the mic through the USB port. 

The draw back is that you must change the default back to System (Alsa Mixer) for playback, but the sound is great!

I would like to see plug & play work a lot better of USB mics in the next release of Ubuntu... *hint* *hint*

BTW, I'm using 7.10 Gutsy. 

Happy Recordings!

---

