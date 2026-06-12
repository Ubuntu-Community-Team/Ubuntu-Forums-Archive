---
title: "Those Funny Funguloids - GetDeb - Scratchy audio help"
date: 2007-11-12
forum: Gaming &amp; Leisure
---

### Post by BigSilly on 2007-11-12
Just downloaded TFF from GetDeb as per the thread title, but I'm getting really poor scratchy audio. Does anyone know what could be causing this? I've had it before when using GetDeb, last time I got it was when I downloaded Glest.

What's the fix for this? Thanks in advance. :)

---

### Post by weblordpepe on 2007-11-12
Wow random! 

I downloaded Funguloids too. But the audio kept skipping on me and it was using lots of CPU. So I uninstalled it. A shame really because its got nice graphics.

---

### Post by BigSilly on 2007-11-12
Can't say I've noticed that, just this audio problem for me really. Any ideas before I remove it?

---

### Post by mh114 on 2007-11-13
Here's something on the topic, from the INSTALL file: :)
```
SETTING UP AUDIO OUTPUT
-----------------------

  Getting audio output to work on Linux can be a pain! Today ALSA is the sound
  system of choice and comes with "legacy support" for OSS, the old (Linux)
  interface for audio output via /dev/dsp. While ALSA supports multiple sound
  sources (applications doing audio output simultanously) and a lot of other
  gimmicks, it still has to be set up (although the defaults are rather
  resonable)!
  My first advice is to simply try it. Start Funguloids and if you have sound
  output everything is fine. If not, read on ;-)
  However, this is not the place to go too deep into all those details but a
  few words might save you some headaches. I assume that some sort of sound
  output already works on your system (like playing back MP3s).
  One basic problem is that only one application can use the sound hardware. If
  your desktop manager uses a 'sound daemon' of some kind (like esd or artsd)
  this daemon has already connected to your sound card and allows no other
  application to do audio output. Note that this is not only true for 'sound
  daemons'. Every application that does sound output directly to the sound card
  will block the hardware). In this case you can 1) either stop the sound
  daemon, 2) tell Funguloids to use this sound daemon or 3) configure ALSA to
  allow more than one applications to connect to the sound hardware.
  Option 1) should be clear. Everytime you want to play Funguloids you
  have to stop the sound daemon and start it again after you finished. This is
  not really convenient and not neccessary in most cases. 2) With OpenAL sound
  rendering you can tell OpenAL to use the sound daemon. You do this by creating
  a configuration file in your home directory named '.openalrc'. This file
  should at least contain the following line:
    (define devices '(SOUNDDEVICE))
  with SOUNDDEVICE being one (or a space-separated list) of 'alsa', 'esd',
  'arts', 'sdl', or 'native'. Search the web for more informations about the
  '.openalrc'. To my knowledge there is no current official documentation for
  this file. Please correct me if I'm wrong.
  Option 3) can be achived by either using hardware that supports sound mixing
  ('SB Live' comes to my mind) or using ALSA's 'dmix' plugin. With a recent
  ALSA library you can simply specify
    (define alsa-out-device "plug:dmix")
  in your '.openalrc'. However, all applications that are supposed to do audio
  output at the same time must use 'plug:dmix' or else it won't work. This can
  be remedied by defining ALSA's 'default' device to be 'plug:dmix', so that
  all recent (ALSA >= 1.0) applications do so be default. You can put your
  configuration into $HOME/.asoundrc or system-wide in /etc/asound.conf.
  For details have a look in the ALSA wiki at http://alsa.opensrc.org/,
  notably http://alsa.opensrc.org/.asoundrc and http://alsa.opensrc.org/Dmix

  If you have choosen FMOD Ex for audio rendering, you can tell it to use ALSA
  or OSS. In Funguloids' configuration file 'gamesettings.cfg' you can set
  the option 'fmod_use_alsa' to 'on' fpr ALSA output and 'off' for OSS. The
  default is to use ALSA.


  Clicks, pops and scratching sound
  ---------------------------------
  Even if you have audio output working you might get some 'noise' / clicking /
  popping sound (you name it). This is encountered by more than a few people
  and is in my experience always caused by sample rate mismatch. For example
  your sound card is fixed to a sample rate of 48 kHz and you are playing back
  audio data with a sample rate of 44,1 kHz (quite common since DVD audio is at
  48kHz and CD audio is at 44,1 kHz). During playback the sound system has to
  convert 44,1 to 48 kHz. When this isn't done carefully you end up with single
  samples just not 'fitting together' - and producing the dreaded clicks. While
  the actual resampling isn't the problem, the timing is. Again, search the web
  for details. You can set up ALSA to do explicit sample
  rate conversation or tell dmix to use your preferred sample rate (dmix'
  default sample rate is 48 kHz). However, while this might fix the clicks for
  one sample rate it might break the other so do some testing until you are
  happy with both. I cannot give a simple solution as the details depend on
  your hardware but you should start setting dmix' 'rate' option to 44100 and
  try different values for the configuration options 'period_size' and
  'buffer_size' as they are the keys. And make sure you have read the wiki
  pages mentioned above.

```

---

### Post by BigSilly on 2007-11-13
I fear I shall never remember to check text files after installing stuff! Thanks for the heads up. I'll check my settings.

---

### Post by weblordpepe on 2007-11-14
Maybe I should go RTFM too :(

---

