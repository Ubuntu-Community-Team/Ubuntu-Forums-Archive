---
title: "Function Generator for soundcard"
date: 2006-11-27
forum: Education &amp; Science
---

### Post by HAARP on 2006-11-27
Hi there,
I need a Linux software capable of generating functions (sine, square, etc.) and outputting them to the soundcard. Id would also be useful if it could use a higher sample rate (48kHz or 96kHz).
I can't seem to find any. Thanks (:

---

### Post by HAARP on 2006-11-27
Found one:
[http://www.comp.leeds.ac.uk/jj/linux/siggen.html](http://www.comp.leeds.ac.uk/jj/linux/siggen.html)

---

### Post by LevTermen on 2006-11-27
Hi,

You'll find your wave generators on the following audio editors: [Audacity]("http://audacity.sourceforge.net/") or [Sweep]("http://www.metadecks.org/software/sweep/").

If you like the block diagram way of chaining signals like NI Labview or Mathworks Simulink provide, [PureData]("http://puredata.info/") might do the job too.

Should your thirst still have to be quenched, please refer to: [http://linux-sound.org/]("http://linux-sound.org/"), especially its "Scopes" category.

All the aforementioned apps are apt-gettable under Ubuntu, provided you enable the relevant multiverse/universe repositories.

I've also succesfully been able to use the [REFerence Audio CD]("https://sourceforge.net/projects/refacd/") for room impulse extraction.

And if I don't seem to be of help, then you might wanna check another third-party forum hosted here, [Ubuntu Studio]("http://www.ubuntuforums.org/forumdisplay.php?f=128").

Lev, heterodyning...

---

### Post by HAARP on 2006-11-27
What I needed was a simple generator to output some stuff to the soundcard. Audacity is fine, but seems to be limited to 20kHz, so I was looking for alternatives. That's also why I need to boost the sample rate.
SigGen does this just fine, and is simple enough for me to use. I'm just an amateur trying to test his electronic abominations with different signals and waveforms ;) Thanks anyway!

Not related to my initial question, but REFerence Audio CD looks like it could be useful.
Thanks!

---

### Post by LevTermen on 2006-11-27
OK I didn't even try to understand why you wanted to increase the sampling rate, back to the good ol' Nyquist/Shannon issue.

I am to do some amateurish audio/electronic attempts too, but I quite fear I might waste my soundcard when used as signal analyzer. Have you considered the USB scope solution? For example: [http://www.usb-instruments.com/]("http://www.usb-instruments.com/") (no advertisement intended). Or at least some homemade optoisolated security?

Oh, and don't miss Fons Adriansen's Aliki for room impulse measurement if that's what you're into:
[http://lac.zkm.de/2006/papers/lac2006_fons_adriaensen_01.pdf]("http://lac.zkm.de/2006/papers/lac2006_fons_adriaensen_01.pdf")
[http://lac.zkm.de/2006/presentations/lac2006_fons_adriaensen_01_slides.pdf]("http://lac.zkm.de/2006/presentations/lac2006_fons_adriaensen_01_slides.pdf")
[http://users.skynet.be/solaris/linuxaudio/]("http://users.skynet.be/solaris/linuxaudio/")

I'd take a look too at his Jaaa and Jnoise jack applications for signal analysis and noise generation.

---

### Post by HAARP on 2006-11-28
You seem to have quite a knowledge about this subject, that's impressive!

I'm not really interested in USB stuff. However, I am planning to use my soundcard as a signal analyzer/signal source. I will use optocouplers to save my soundcard from any destruction, but it's still being worked on. The actual buffer will use the IL300 coupler, which is one of the few that are capable of coupling analog signals. The only problem I have so far, is figuring out how to make the input capable of probing both 230V (mains) or 230mV (low voltage) without destruction. If you're interested in my circuit so far, tell me, I'll show you how I plan to do it.
Of course, putting the coupler after the analog/digital-converter would be a far better solution, but I wouldn't be able to use my soundcard with this. I'm planning to do this as a DIY-project, so designing my own A/D-board seems to be a bit over-the-top. Hence no USB/LPT/whatever.
Besides, I've yet to find a Linux oscilloscope software that can read from USB/LPT. Currently I use [osqoop](http://lsn.unige.ch/osqoop/), which is a pretty simple application, but does the job just fine.  (They even have a Debian/Ubuntu repository) I also tried xoscope, but it didn't satisfy me. [quoscc](http://flup.homelinux.org/qoscc.html) seems to be a good application, too. But somehow, I prefer Osqoop.
I believe my soundcard (Audigy 2 ZS) should suffice to get a useful quality.

Oh well, we'll see :)
bye, Haarp

---

### Post by TestGuru on 2009-05-22
how about this one, [www.multi-instrument.com/MIsetup.zip]("http://www.multi-instrument.com/MIsetup.zip")

---

### Post by DarrenCT on 2010-07-22
> **TestGuru said:**
> how about this one, [www.multi-instrument.com/MIsetup.zip]("http://www.multi-instrument.com/MIsetup.zip")

Not sure, but I don't think this is a Linux (or Ubuntu) solution.

---

