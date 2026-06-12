---
title: "Nobody responding. . . please help"
date: 2006-03-04
forum: Desktop Environments
---

### Post by JDavid5381 on 2006-03-04
My CD's were playing fine using Sound Juicer, and the CD Player, but now the same CD's and other mp3's that I was able to play before, aren't playing. When I try and play a song or mp3 file on the CD Player, Sound Juicer, and even Rythmbox they won't play and I get an Error alert saying "Error playing CD, Reason: could not open resource for writing." Help. . . I'm new to Ubuntu and Linux.

-James

---

### Post by localzuk on 2006-03-04
My guess would be that you don't have permission to use the audio device.

From a Terminal, run this:

```

groups

```

And post the result here

---

### Post by JDavid5381 on 2006-03-04
Hey this is what I got when I ran "groups" on the CLI: adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin

I'm the only administrator on my laptop.

---

### Post by localzuk on 2006-03-04
Well, I'm afraid that has me stumped... It likely still has to do with device permissions but I do not know any more than that. Sorry. Hopefully someone else will be able to advise.

---

### Post by lyricmuse on 2006-03-04
Is it possible that in some way your cd isn't mounted???  I'm a newbie so I'm just guessing here.  Or it's possible your cdrom just died.

---

### Post by akiro.yamamoto on 2006-03-04
This sounds like a sound card error. Did you make any changes to your sond card
set-up. Try specifying Alsa , OSS or ESD and check for sound playback.

---

### Post by JDavid5381 on 2006-03-05
I went into Multimedia Systems Selecter and checked my audio set-up.  I tested the different options like OSS, ESD, and ALSA.  what was strange was that when I tried testing ESD I got an Error alert saying "Failed to construct test pipeline for ESD."  Could this have anything to do with it, or am I way off?

-James

p.s. how do I access my sound card set-up? or is that what I did just then?

---

