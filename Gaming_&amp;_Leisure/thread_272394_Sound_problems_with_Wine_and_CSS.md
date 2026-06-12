---
title: "Sound problems with Wine and CSS"
date: 2006-10-06
forum: Gaming &amp; Leisure
---

### Post by ubu-for on 2006-10-06
Everytime I start winecfg, I get this terminal error message and "Counter-Strike: Source" lags only when I turn on the sound in winecfg, too.

```
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
```

I have a "Abit KN8 SLI" mainboard. Please HELP!

THX!

---

### Post by deanhopkins on 2006-10-06
Change the sound driver in winecfg to OSS.


Do you mind giving me a few tips on running CSS fine once you fix your problem mate?

---

### Post by ubu-for on 2006-10-06
I've already tried every sound option, but only without sound the lags disapear. So it must be a hardware problem with Wine.

Post the link to your thread and I will do my best.

---

### Post by ubu-for on 2006-10-06
Terminal error message if OSS on:

```
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
```

---

