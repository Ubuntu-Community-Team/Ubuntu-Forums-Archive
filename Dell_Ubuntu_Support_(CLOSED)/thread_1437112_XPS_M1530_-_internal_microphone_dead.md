---
title: "XPS M1530 - internal microphone dead"
date: 2010-03-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by btnz on 2010-03-23
Hi, I'm running ubuntu 9.10 on a m1530 laptop.
Unfortunately the built-in microphone doesn't seem to work at all: Monitoring the input level or using the recorder, skype, whatever, it's dead.

I tried several different settings with the audio-panel, to no avail.
Audio playback works just fine.
Currently I'm using the setting Analog Surround 4.0 Output + Analog Stereo Input (other settings are digital stereo duplex/ output with analog in).
One internal sound device is displayed ("1 in/1 out").

```
lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```pulseaudio is version 0.9.19.
installing linux-backports-modules-alsa-karmic-generic did not help.

a bit disturbing:
```
alsactl init
Unknown hardware: "HDA-Intel" "SigmaTel STAC9228" "HDA:83847616,1028022e,00100402" "0x1028" "0x022e"
Hardware is initialized using a guess method

```

at the sound settings menu -> input I can choose between micro 1 and micro 2.
one *very weird* thing is that regardless which I select, it appears to expect input from the plug for the external mic at the front: if I plug in my headphones there (no ext. mic available..), the input level monitor responds.

So basically it looks like my internal mic is just not found. Or somehow not available for selection.

please help, greets

---

### Post by btnz on 2010-03-23
okay, so I figured it out now...turns out that the combination of the standard gnome volume manager and alsa/the m1530 mic is a complete ****-up.

When the "Input" is changed in the volume manager, the alsa input source 0 is set to either "Mic" or "Front Mic". Front Mic is the actual plug for an external mic. Now unfortunately "Mic" is not what we need here, the desired option would be "Digital", but we can get this through our pretty gnome interface.

So, the solution is to run ```
alsamixer -Vc
``` to show us the capturing devices and select "Digital" as the first input source. Oh, and while you're there, turn up the volume..

Concerning the low input level often observed, I found padevchooser to be very handy, allows you to boost the input level to up to 480% instead of the lousy 150% you get out of gnome-volume-control.

I'd be interested to hear if someone has an idea how this actually got this messed up!

---

### Post by bloodorange on 2011-01-06
Hi btnz.

Is your microphone still working?  I've started a thread (before someone pointed me to yours) about the same problem I'm having with Maverick and my XPS M1530.  ([http://ubuntuforums.org/showthread.php?p=10322423#post10322423]("http://ubuntuforums.org/showthread.php?p=10322423#post10322423"))

As you can see from this screen shot, I've selected Digital as an input, but it still doesn't show up in Sound Preferences so that I can choose it there.  I've even tried making all the three middle inputs (as shown in alsamixer) to Digital.  Also, I can't see where, in alsamixer, to turn-up the Digital input as you suggest.

[IMG]http://dl.dropbox.com/u/1098200/alsamixer.png[/IMG]

Needless to say, I still can't get the internal microphone to work.

---

### Post by NotJustANewbie on 2011-01-07
I'm in the same position... PLEASE HELP!

---

