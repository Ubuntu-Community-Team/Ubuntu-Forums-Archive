---
title: "No sound in games."
date: 2005-05-26
forum: Gaming &amp; Leisure
---

### Post by fjleal on 2005-05-26
Hi.
I tried a few games on a recently-installed Hoary: TORCS, UT2003 demo and UT2004 demo. None of them produces any sounds. In TORCS, the sound option isn't even there. Apart from the games, all system sounds seem to be ok. In the Multimedia Systems Selector, I get three systems: ALSA, ESD and OSS - no matter which one I choose, still I get no sound in games, but I can play CDs, DVDs, video, the Gnome sounds, everything else.

Any ideas what the problem may be? Thank you.

Edit: error in CLI is: "/dev/dsp: device or resource busy." :(

---

### Post by MrTom on 2005-05-26
Your problem is the fact that only one program can use /dev/dsp (your soundcard) at a time, to get around this problem a software layer is used to mix the sound together then output it to the soundcard. Ubuntu uses a software layer called ESD.

Your games want to write directly to the soundcard - ESD blocks them.
My method of getting round this is to change the ESD config so that it blocks the sound card only when it needs to
run:
```

sudo gedit /etc/esound/esd.conf

```

and change 
auto_spawn=0
to
auto_spawn=1

Then in 'sound preferences' untick sound server enabled at startup. 

Hope this works ok, the sound effects in GNOME will be disabled but all the other sound playing apps work.

---

### Post by fjleal on 2005-05-27
Hi, thanks for the answer. I forgot mentioning that I had already tried killing esd, to no success. Something else must be using /dev/dsp...

EDIT: killed a few processes, and find out that sound works after killing esd. Another way around it is doing «echo "(define devices '(sdl))" > ~/.openalrc» - I'm not quite sure what it does, got it from the ut2003deom readme, but this way I have sound without killing esd. TORCS is the only one that didn't understand this... ;)

---

