---
title: "Upgrade to 8.10 and Sound Issues"
date: 2009-03-06
forum: Gaming &amp; Leisure
---

### Post by epitaph on 2009-03-06
First I will warn that this probably isn't for the light-hearted. Proceed at your own risk.

I upgraded to 8.10 for various reasons earlier today and had quite a few issues, but I've ironed most of them out and now I'm down to just one and it involves sound and gaming.

First, some background information:

I completely disabled Pulseaudio (again, why the heck did it get installed during the upgrade?!) and that fixed the huge issues with sound lag. Next I made sure that devices weren't stealing /dev/dsp entirely which checked out. I can watch movies in VLC, listen to music in Banshee and watch flash movies on youtube without issue (all at once).

ChallengeQuake3 (customized Quake3 client) works fine, though the sound quality seems less crisp than it did on 8.04 (if that makes any sense). There may be a very slight delay to the sounds, though hardly noticeable.

UT2004 had no working sound after upgrading. I created symlinks from libSDL-1.2.so.0 and openal.so to the shared libraries in /usr/lib/ and all this allows me to do is launch the game using "aoss ut2004" which yields considerable sound lag, poor positioning and static-laden sound.

Am I possibly linking to the wrong libraries? Example:

```

libopenal.so.1
libopenal.so.1.3.253
libSDL-1.2.so.0
libSDL-1.2.so.0.11.1
libSDL_image-1.2.so.0
libSDL_image-1.2.so.0.1.5

```

The above are all in /usr/lib/, how can I tell which one to use? Or does it matter?

Second part involves the .openalrc configuration file. Mine is as follows:

```

(define devices '(alsa))
(define alsa-device "default")
(define speaker-num 2)
(define sampling-rate 44100)

```

The behavior doesn't appear to change if I change the alsa-device to "Intel" (which is my device) or if I change it to (alsa null) in the first line which yields no sound even if I use "aoss ut2004" to launch the game.

Now, the truly odd thing is I get a:

```

$ ut2004
open /dev/[sound/]dsp: Device or resource busy

```

Whereas I did not get that after creating the symlinks and editing the .openalrc file on 8.04.

I know this was a lot to stomach, but it is really driving me crazy. Any help is appreciated.

[edit] I gave up and just went back to using my old Audigy2 ZS so I had hardware mixing. Still not sure why it wouldn't work anymore.

---

