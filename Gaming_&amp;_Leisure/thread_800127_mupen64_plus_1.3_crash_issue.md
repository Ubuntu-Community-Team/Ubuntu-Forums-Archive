---
title: "mupen64 plus 1.3 crash issue"
date: 2008-05-19
forum: Gaming &amp; Leisure
---

### Post by rocky5051 on 2008-05-19
I recently downloaded it, and when I try to run a rom, it crashes, and you have to restart the program. I haven't any lead on why, because I used the same video plugin as was supplied with the normal version of mupen64 (gln64 0.4.1).

Also, on the note of video plugin, Rice's Video Plugin always seems to crash (on both mupen64 and mupen64plus), and I can't figure out why for those, either.

Anyway, mupen64 0.5 works as it should but I would really like to try the plus version, as I heard it had a good amount of linux enhancements.

I'm using the restricted nvidia drivers (version 96.43.05) with an nVidia GeForce 4000MX PCI graphics card. I also have NVCLOCK but having it disabled or enabled didn't make any difference.

Thanks for any help :KS.

---

### Post by argor on 2008-05-21
try this bulds  [http://www.emutalk.net/showthread.php?t=44392](http://www.emutalk.net/showthread.php?t=44392)

---

### Post by westplastic on 2008-06-02
I had a similar issue where running any ROM would immediately crash mupen64plus.  However, if you run mupen64plus from the terminal, you'll be able to see some feedback from the program.  The last few lines before it crashed again indicated that my problem was with the audio:

```
$ mupen64plus
...
(II) JttL's sound plugin version 1.3
(II) Initializing SDL audio subsystem...
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
(II) Allocating memory for audio buffer: 65536 bytes.
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
(EE) Couldn't open audio: No available audio device
```

For whatever reason, closing Rhythmbox fixed that problem.

---

### Post by argor on 2008-06-03
thae have fix this bug in this bulds [http://www.emutalk.net/showthread.php?t=44392](http://www.emutalk.net/showthread.php?t=44392)

---

