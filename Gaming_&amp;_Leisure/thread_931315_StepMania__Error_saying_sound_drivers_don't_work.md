---
title: "StepMania : Error saying sound drivers don't work"
date: 2008-09-27
forum: Gaming &amp; Leisure
---

### Post by Ephemeral on 2008-09-27
Hello hello,

I posted in Multimedia & video on a sound issue :
[http://ubuntuforums.org/showthread.php?t=930822](http://ubuntuforums.org/showthread.php?t=930822)

But now, StepMania doesn't run, I tried running it in Terminal to see if I could get an error message and this is it :

```
eternal@eternal-desktop:~/otherprograms/StepMania-3.9$ ./stepmania
StepMania 3.9
Log starting 2008-09-27 13:08:59
Loading window: gtk
OS: Linux ver 020624
Crash backtrace component: x86 custom backtrace
Crash lookup component: dladdr
Crash demangle component: cxa_demangle
Runtime library: glibc 2.7
Threads library: NPTL 2.7
TLS is available
ALSA: Advanced Linux Sound Architecture Driver Version 1.0.16.
ALSA Driver: 0: HDA Intel [Intel], device 0: ALC882 Analog [ALC882 Analog], 0/1 subdevices avail
ALSA Driver: 0: HDA Intel [Intel], device 1: ALC882 Digital [ALC882 Digital], 1/1 subdevices avail
Couldn't load driver ALSA: dsnd_pcm_open(hw:0): Device or resource busy
Mixing 0.000000 ahead in 0 Mix() calls
Couldn't load driver ALSA-sw: dsnd_pcm_open(hw:0): Device or resource busy
Mixing 0.000000 ahead in 0 Mix() calls
Couldn't load driver OSS: RageSound_OSS: Couldn't open /dev/dsp: Device or resource busy
Language: english
Theme: default
Error: Couldn't find a sound driver that works

```

So either the sound drivers aren't working properly, because these ones are supposed to let me use different applications at the same time, or something else is using the sound and StepMania needs it.

Any idea?

---

### Post by Kjalvalr on 2008-11-07
Open your StepMania Folder, open the Data Folder, and open the StepMania.ini File. Find the Line: SoundDevice= and type 'default' after it. That's as far as my Knowledge goes, so hopefully that solves your Problem.

---

