---
title: "XPS M1710 - Can't record - sound settings"
date: 2007-09-17
forum: Dell  Ubuntu Support
---

### Post by FreeSoul on 2007-09-17
Hello all,

     Well, I'm almost running linux 100% but i still have to switch to windows to get skype (sound recording) to work. Please help me to get away from Microsoft!
     
     I don't have alsa mixer installed but had in the past and it didn't help. When I go to System - preferences - sound the first 3 of 4 tests work to hear sound. (first three are on auto detect). But the last test "sound capture" doesn't work. 

I get this message:
> "Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'"

     If your capture is working (especially with the same laptop) can you share your settings with me under "sound capture" and also after that, what is he name of your device. (I've tried all combos and nothing, so really I'm looking for a fix AND your settings :-) )

My sound capture drop down menu includes:
stac92xx analog or digital
ALSA
OSS
test sound
silence

My device choices are either 1. siigmatell stac 9200 (OSS Mixer)
or 2. HDA Intel (Alsa Mixer)

Thanks,
FreeSoul

---

### Post by FreeSoul on 2007-09-17
I got it!

Today is a very special day indeed. I can say I'm now 95% over to Linux.
By the way the fix was something I should have tried a while ago.
I just edited "/etc/modprobe.d/alsa base" and added this line at the end "options snd-hda-intel model=ref"
(You must restart the computer.)

FreeSoul

---

