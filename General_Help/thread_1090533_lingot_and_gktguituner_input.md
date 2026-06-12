---
title: "lingot and gktguituner input"
date: 2009-03-08
forum: General Help
---

### Post by bryncoles on 2009-03-08
hi folks. i recently noticed that my gtkguituner had stopped accepting audio input, from my laptops built-in mic. i tried reinstalling it, and i tried installing lingot and neither accept input, nor seem to have any settings i can fiddle with till they do. 

annoyingly, they dont give any error messages either. they just sit thgere, lifeless and impotent, taunting me with their not-telling-me-what-note-i-just-played...

anyone got any idea how we can trouble-shoot / resolve / revitalise these tuners?

im running intrepid on a dell inspiron 1525n.

---

### Post by bryncoles on 2009-03-09
well, i fiddled and fiddled and not gtkguitune seems to work again... but no use with lingot. how do w configure that damn thing? seems to have no option for selecting inputs...

---

### Post by cgatica on 2010-02-17
I don't have the answer, bummer.

I'm using Karmic Koala.

I've installed both and none of them seems to work for me.
Lingot seems not to receive the input i've defined on "sound preferences" (it showed that the mic was working).
Gtkguituner does the same, not showing any of the sources in the "recording input" option.

I'm suspecting it's somekind of driver/config issue with the webcam (that has a mic built in). Eventough "Cheese webcam booth" manages to record video and sound from this source. weird.

```

> lsusb
Bus 002 Device 003: ID 05a9:8519 OmniVision Technologies, Inc. OV519 Webcam
> ls /dev/audio*
/dev/audio  /dev/audio1

```

If there's someone with good ideas outthere, please reply.

---

### Post by Slave2Metal on 2010-02-28
Was having issues with lingot, until now.  It would always crash and the needle was always bouncing around at the slightest sound.  So today I increased the noise threshold and seems to be working great with no crashing. Those of you that have tried lingot and it kept crashing, try doubling the noise threshold in options.  Using version 0.7.4 at the moment.

---

### Post by nealman13 on 2010-05-14
If you have /dev/audio and /dev/audio1, then lingot may be picking up the input from the wrong audio device.

Try editing ~/.lingot/lingot.conf and changing this line:

AUDIO_DEV = /dev/dsp

to this:

AUDIO_DEV = /dev/audio1

Then restart lingot and see if it works.

---

### Post by gnuts on 2011-01-14
I'm not sure if you are still looking, but I sorted this out. on the capture page of lingot preferences change Audio dev to default, and in ~/.lingot/lingot.conf change the line:

AUDIO_DEV = /dev/dsp

to 

AUDIO_DEV = /dev/snd

works like a charm for me now

ubuntu 10.10 64bit

---

