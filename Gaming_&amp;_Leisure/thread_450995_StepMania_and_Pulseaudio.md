---
title: "StepMania and Pulseaudio"
date: 2007-05-21
forum: Gaming &amp; Leisure
---

### Post by Extrudedaluminiu on 2007-05-21
Hi,

Has anyone around here gotten StepMania to run and play sound while Pulseaudio is running?

Thanks,

---

### Post by harrisony on 2007-05-26
I have a really hacked up hack which is really hacky
```
sudo padsp /opt/stepmania/stepmania
```
i followed this guide and it works [http://blog.paulbetts.org/index.php/2007/04/15/pulseaudio-in-ubuntu-feisty-play-sound-over-the-network/](http://blog.paulbetts.org/index.php/2007/04/15/pulseaudio-in-ubuntu-feisty-play-sound-over-the-network/)

---

### Post by Extrudedaluminiu on 2007-05-27
What version of StepMania did you try?

When I tried StepMania under padsp, I get this error:

> 
StepMania CVS 4.0 CVS
Log starting 2007-05-27 00:13:29
Loading window: gtk
OS: Linux ver 020618
Crash backtrace component: x86 custom backtrace
Crash lookup component: dladdr
Crash demangle component: cxa_demangle
Runtime library: glibc 2.3.6
Threads library: NPTL 2.3.6
libavcodec: 0x332800 (3352576)
TLS is available
/////////////////////////////////////////
WARNING: OSS_GETVERSION failed: Invalid argument
/////////////////////////////////////////
Sound driver: OSS
Lights driver: SystemMessage
Lights driver: Export
ptrace failed: Operation not permitted
ptrace failed: Operation not permitted
ptrace failed: Operation not permitted
Crash handler failed: "b->ref >= 1" while still in the crash handler

StepMania CVS has crashed.  Debug information has been output to

    /tmp/crashinfo.txt

Please report a bug at:

    [http://sourceforge.net/tracker/?func=add&group_id=37892&atid=421366](http://sourceforge.net/tracker/?func=add&group_id=37892&atid=421366)


---

### Post by harrisony on 2007-05-28
i use v3.9 but i would post a message on the forums and file a feature request for pulseaudio support :)
be sure to post the links here as well if you do so others can follow :)

---

### Post by MaX on 2007-09-11
> **harrisony said:**
> I have a really hacked up hack which is really hacky
```
sudo padsp /opt/stepmania/stepmania
```
i followed this guide and it works [http://blog.paulbetts.org/index.php/2007/04/15/pulseaudio-in-ubuntu-feisty-play-sound-over-the-network/](http://blog.paulbetts.org/index.php/2007/04/15/pulseaudio-in-ubuntu-feisty-play-sound-over-the-network/)

Well that didn't work... I'm in Gutsy now.
```
StepMania 3.9
Log starting 2007-09-12 01:05:05
Loading window: gtk
OS: Linux ver 020622
Crash backtrace component: x86 custom backtrace
Crash lookup component: dladdr
Crash demangle component: cxa_demangle
Runtime library: glibc 2.6.1
Threads library: NPTL 2.6.1
TLS is available
ALSA: Advanced Linux Sound Architecture Driver Version 1.0.14 (Thu May 31 09:03:25 2007 UTC).
ALSA Driver: 0: NVidia CK804 [CK804], device 0: Intel ICH [NVidia CK804], 0/1 subdevices avail
ALSA Driver: 0: NVidia CK804 [CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958], 1/1 subdevices avail
Couldn't load driver ALSA: dsnd_pcm_open(hw:0): Device or resource busy
Mixing 0.000000 ahead in 0 Mix() calls
Couldn't load driver ALSA-sw: dsnd_pcm_open(hw:0): Device or resource busy
Mixing 0.000000 ahead in 0 Mix() calls
Couldn't load driver OSS: RageSound_OSS: Couldn't open /dev/dsp: Connection refused
Language: english
Theme: default
Error: Couldn't find a sound driver that works

```

---

### Post by KillMyBrain on 2007-09-12
Never bothered, but good luck with it.

---

### Post by hikaricore on 2007-09-12
You'll need to kill pulseaudio before starting stepmania or it will not work.

I've found no work arounds for it otherwise.

---

### Post by rstets on 2009-01-29
```
pasuspender ./stepmania
```

worked for me

---

### Post by hikaricore on 2009-01-29
It's probably worth mentioning that in Intrepid I'm having no trouble with pulse and Stepmania.

---

### Post by Crafty Kisses on 2009-01-31
Same here my good friend, it works perfect in Intrepid.

---

### Post by Halow on 2009-03-05
While it does run while Pulseaudio is also running (using Inretpid), it tends to jam up the sounds, so to speak. I use two sound cards for different things essentially at all times (which makes me love PA, as it's easy to manage which streams go through which card quite easily). Anything PA sends through my mobo's card while Stepmania is running becomes queued up, but not played. Stepmania doesn't show a stream in PA's volume control.  Running ```
padsp $PREFIX/stepmania
``` causes it to crash before fully loading. I did try it out with ```
sudo padsp $PREFIX/stepmania
``` and it loaded an ran, but never did run *through* PA, which is what I'd like it to do.

---

### Post by unimatrix on 2010-01-17
So here are the possibilities (assuming you've installed Stepmania from [PlayDeb.net]("http://www.playdeb.net/software/StepMania") on Ubuntu 9.10 Karmic Koala)

```
sudo padsp `which stepmania4`
```
This worked best for me. Unfortunately it is necessary to run it from terminal (and not from the main menu) due to the password requirement. Using gksudo instead of sudo does not work.
EDIT: Getting sound corruption with this too.

```
pasuspender stepmania4
```
Does work, but the sound can be all jittery.

```
aoss stepmania4
```
Same as the previous option. Works, but sound can get really corrupted.

---

