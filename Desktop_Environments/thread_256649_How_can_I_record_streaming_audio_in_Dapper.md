---
title: "How can I record streaming audio in Dapper"
date: 2006-09-13
forum: Desktop Environments
---

### Post by mister_p_1998 on 2006-09-13
Ok Ive got a duplex soundblaster PCI card, when I try to record streaming audio in Audacity, theres no sound coming into the program, I cant seem to choose currently playing audio.

---

### Post by reclusivemonkey on 2006-09-13
> **mister_p_1998 said:**
> Ok Ive got a duplex soundblaster PCI card, when I try to record streaming audio in Audacity, theres no sound coming into the program, I cant seem to choose currently playing audio.

Have a play around in Gnome Mixer, I can usually get it by unmuting "wave". Sorry I can't be more specific I am at work, I will check back when I get home.

Also, you could try the "dumpstream" option in mplayer... It doesn't work with all streams, but does with some.

---

### Post by mister_p_1998 on 2006-09-15
Whats Gnome Mixer?
is it just the standard volume prefs?
Steve

---

### Post by reclusivemonkey on 2006-09-15
> **mister_p_1998 said:**
> Whats Gnome Mixer?
is it just the standard volume prefs?
Steve

Right click on the volume slider on the panel, and its on there somewhere. Again, I am at work so I can't check it. I *think* its the same as Alsa mixer, only slightly easier to use.

---

### Post by haiku99 on 2006-10-05
I've been trying to do the same, after mch web surfing found a REALLY simple way to do it from a terminal window, works perfectly:

[B]bill@bill-laptop:~$ rec sample.ogg
Send break (control-c) to end recording[/B]

after you stop recording the file will be found in your home folder. rec has many option, as folows:

[B]bill@bill-laptop:~$ rec -h
Usage: rec [OPTION]... FILE [EFFECT]...
Play/record sound files to/from unix style sound devices.

  -c, --channels=CHANNELS      specifies the number of sound channels in FILE
  -d, --device=DEVICE          use DEVICE for input/output
  -f, --format=FORMAT          specifies bit format of sample
                               FORMAT is either s, u, U, A, a, or g
  -r, --rate=RATE              sample rate in hertz of FILE
  -s, --size=SIZE              interpret size of sample
                               SIZE is either b, w, l, f, d, or D
  -t, --type=TYPE              specifies file format of FILE
  -v, --volume=VOLUME          change amplitude
  -x, --xinu                   reverse bit order of sample
                               (only works with 16-bit and 32-bit integer data)
      --file                   next argument is FILE
  -h, --help                   display this help and exit
      --version                output version information and exit
      --silent                 do not display filename of currently played file

EFFECTs are one or more of the following:  avg, band, chorus, copy, cut,
deemph, echo, echos, flanger, highp, lowp, map, mask, phaser, pick, polyphase
rate, repeat, resample, reverb, reverse, split, stat, vibro.

See sox man page for detailed information on supported file types, data
formats, and effect options.[/B]

---

