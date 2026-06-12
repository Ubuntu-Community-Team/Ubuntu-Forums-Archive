---
title: "Best Game in the world: Stepmania!.. But it's not working :("
date: 2007-01-06
forum: Gaming &amp; Leisure
---

### Post by nsabatino on 2007-01-06
Hey guys,

I'm having issues running the latest Stepmania binary. When I run it without specifing any specific sound driver, it loads fine, but with no sound and i get the error:

```
ALSA Driver: 0: NVidia CK804 [CK804], device 0: Intel ICH [NVidia CK804], 1/1 subdevices avail
ALSA Driver: 0: NVidia CK804 [CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958], 1/1 subdevices avail
Couldn't load driver ALSA: Not enough substreams for hardware mixing, using software mixing
ALSA: Software mixing at 48000hz
Sound driver: ALSA-sw

```

When I specify OSS as the sound driver in the ini file, it crashes and I get:

```
Couldn't load driver OSS: RageSound_OSS: ALSA detected.  ALSA OSS emulation is buggy; use ALSA natively.
Language: english
Theme: default
Error: Couldn't find a sound driver that works
```

And when I specify ALSA as the sound driver in the ini file, it crashes and I get:

```
ALSA: Advanced Linux Sound Architecture Driver Version 1.0.12rc1 (Thu Jun 22 13:55:50 2006 UTC).
ALSA Driver: 0: NVidia CK804 [CK804], device 0: Intel ICH [NVidia CK804], 1/1 subdevices avail
ALSA Driver: 0: NVidia CK804 [CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958], 1/1 subdevices avail
Couldn't load driver ALSA: Not enough substreams for hardware mixing, using software mixing
Language: english
Theme: default
Error: Couldn't find a sound driver that works

```

Any suggestions?

Thanks,

-Nick Sabatino

---

### Post by KBcool on 2007-11-24
I'm completely new to Linux and Ubuntu, but I did get my sound working properly with stepmania,(of which I'm a huge fan), by changing the sound driver to "OSS" (without quotes), and downloading the alsa-oss wrapper from the synaptic package manager then running "aoss ./stepmania" in the terminal from the main stepmania directory. Hope this helps. Good luck ;)

---

