---
title: "Speakers have gone quiet, can't seem to get them back to normal."
date: 2009-01-24
forum: General Help
---

### Post by oddparticle on 2009-01-24
My problem is this: Until a couple of days ago, the sound on my laptop worked fine, as did my USB speakers. However, now when I try to listen to music through the USB speakers it is incredibly quiet. I have tried every option in the system->sound->music playback menu, to no avail. I've also tried switching various things off then on again. I didn't want to go messing about with drivers and things on my own too much in case I break things.

I've tested the speakers on a friend's laptop and they worked fine.

The only thing I can think of that might have upset my computer lately is that a few days ago I was having trouble making DVDs play and followed the instructions on this page [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) . 

Any insight on how to get this fixed would be much appreciated :).

Edit: All is well, turned up the master volume in alsamixer and now it's nice and loud.

Edit: Oh no it's not :( after being unplugged & plugged back in, the speakers have gone quiet again and now alsamixer seems to have no effect on them - I turn the master volume up and down and they stay exactly the same.

---

### Post by oddparticle on 2009-01-27
Bump.

---

### Post by oddparticle on 2009-01-27
The speakers are Altec Lansing XT2, and in the sound preferences menu, the only option which makes them work at all is "USB audio OSS" (if I try "USB audio ALSA" I just get an error message when I test them - "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback.").

---

### Post by TheLions on 2009-01-27
did you try pulseaduio?

---

### Post by oddparticle on 2009-01-27
> **TheLions said:**
> did you try pulseaduio?

I did, that just makes it play through my laptop's tinny little internal speakers. At the moment, I can actually get those somewhat louder than my good speakers (since unlike the good ones, they do respond to alsamixer), but they distort horribly and have no bass at all :(.

---

### Post by oddparticle on 2009-01-27
Hmm. OK, I now have them loud again - I set the sound playback to "USB audio OSS", turned the master volume down to 10% in alsamixer, restarted my computer, and then turned the master volume back to 90%. I have no idea why that was necessary, but it has done the trick. I guess I should try to avoid unplugging the speakers...

---

