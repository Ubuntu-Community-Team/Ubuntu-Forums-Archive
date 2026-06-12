---
title: "[SOLVED] no sound in fce ultra or mednafen"
date: 2007-03-30
forum: Gaming &amp; Leisure
---

### Post by unebaguettesvp on 2007-03-30
after a fresh install of fce ultra from synaptic (ubuntu edgy eft amd 64 bit), i get no sound!!! everything else works perfectly! i've been having the same problem with mednafen.

anyway, i can get sound out of gens and zsnes. i have libsdl1.2-debian-all installed. i tried fooling around with mednafen more than i have with fceu. i tried using the oss driver and the alsa driver. i really don't know what else to do.

here is a start up for fceu:



fceu Contra\ \(U\)\ \[\!\].nes 

Starting FCE Ultra 0.98.12...
Loading Contra (U) [!].nes...

 PRG ROM:    8 x 16KiB
 CHR ROM:    0 x  8KiB
 ROM CRC32:  0xf6035030
 ROM MD5:  0x5a5c2f4f1cafb1f55a8dc0d5ad4550e5
 Mapper:  2
 Mirroring: Vertical

Initializing video... Video Mode: 512 x 448 x 32 bpp 

Initializing sound...
 Bits: 16
 Rate: 48000
 Channels: 1
 Byte order: CPU Native
 Buffer size: 1152 sample frames(24.000000 ms)
Quit


as i said before, everything works great except for the sound.

anybody have any ideas?

---

### Post by unebaguettesvp on 2007-03-30
can anybody help?

---

### Post by BoyOfDestiny on 2007-03-30
> **unebaguettesvp said:**
> can anybody help?

I was going to link you to a thread in the mednafen forums, but noticed you had a post in it...

Anyway, has it ever worked for you before? Maybe something like ESD is interfering?

sudo killall esd

makes a difference?

Also check your mednafen config

gedit ~/.mednafen/mednafen.cfg

;Select sound driver.
sounddriver default

;Select sound output device.
sounddevice default

;Sound volume level, in percent.
soundvol 100

;Enable sound emulation.
sound 1

;Specifies the desired size of the sound buffer, in milliseconds.
soundbufsize 32

;Specifies the sound playback rate, in frames per second("Hz").
soundrate 48000

When I run mednafen 

 Initializing sound...
  Using "ALSA" audio driver with device "default":
   Bits: 16
   Rate: 48000
   Channels: 2
   Byte order: CPU Native
   Buffer size: 1536 sample frames(32.000000 ms)

Is shown, you can try setting the default driver to OSS and default device to /dev/dsp

That's what I used before mednafen worked with ALSA... 

I hope this helps you. :)

---

### Post by unebaguettesvp on 2007-03-30
sudo killall esd did the trick!!! in addition to a hard restart of the computer!!!

that was such a pain. thanks!

---

### Post by unebaguettesvp on 2007-03-30
actually. no that didn't work!!!!

urghhhh....

the sound worked for 2 games. then my computer froze (my ubuntu install is constantly crashing and i have no idea why). when i restarted, i tiried to do it again and it didn't work. i tried sudo killall esd. but that didn't do anything.

i don't know anymore.

any other ideas anyone?

---

### Post by unebaguettesvp on 2007-04-02
sorry for the bump but i really want to get this working! i just enjoyed a nice game of Contra WITH SOUND but that was it! one game!!!

that's twice i got the sound to work. both times the sounddriver was set to oss and the sounddevice was set to default.

i'm not editing anything else!!! i swear. i just execute mednafen %s and it worked!

any ideas?!

---

### Post by unebaguettesvp on 2007-10-24
this thread is related to:
[http://ubuntuforums.org/showthread.php?t=470050](http://ubuntuforums.org/showthread.php?t=470050)

which is related to a bug on launchpad:
[https://bugs.launchpad.net/bugs/121433](https://bugs.launchpad.net/bugs/121433)

---

