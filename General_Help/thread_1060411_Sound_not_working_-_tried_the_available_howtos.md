---
title: "Sound not working - tried the available howtos"
date: 2009-02-04
forum: General Help
---

### Post by gruff on 2009-02-04
(8.10) The sound has stopped working completely after a recent update, and I notice that a lot of other people have had the same problem. however the posted fixes don't work for me. 

I have tried fixes relating to ALSA and have also tried getting pulseaudio working, but all seems ok apart from no sound whatsoever coming out of the speakers or headphones.

Here's the output from lspci -v relating to my card:

```
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device 02c5
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 1000 [size=256]
	I/O ports at 1880 [size=64]
	Memory at 74000800 (32-bit, non-prefetchable) [size=512]
	Memory at 74000a00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0
```

And here's the output of lsmod | grep snd

```

snd_intel8x0           37532  4 
snd_ac97_codec        111652  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm

```

So my sound card has been detected and it appears that the correct modules are loaded, but still no sound.

When I run the "Default sound card" application I get 2 options which are I282801DBICH4 and pulseaudio. I282801DBICH4 is currently selected.

See the attached screenshots for what is in my sound preferences.

The volume controls are all set to maximum and nothing is muted.

I have spent quite some time looking into this and am at a loss as to what is wrong. Has anybody got any suggestions?

---

### Post by gruff on 2009-02-06
*bump*

Is there anybody out there who can help?

Please let me know if there is any more info I can provide.

---

### Post by gruff on 2009-02-07
*bump*

I have searched the forums and tried pretty much everything I can find to fix this problem, but it still doesn't work.

Here's the output from aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

When I open an ogg file with alsaplayer I get no errors or other messages, but no sound either.

---

### Post by gruff on 2009-02-07
The output of alsa-info.sh can be seen here:

[http://www.alsa-project.org/db/?f=89b056b86483e6467d9b32054980329e68f2a222](http://www.alsa-project.org/db/?f=89b056b86483e6467d9b32054980329e68f2a222)

---

### Post by dcstar on 2009-02-07
> **gruff said:**
> (8.10) The sound has stopped working completely after a recent update, and I notice that a lot of other people have had the same problem. however the posted fixes don't work for me. 
.......
I have spent quite some time looking into this and am at a loss as to what is wrong. Has anybody got any suggestions?

You may have to try an find out what was updated and roll back the packages to the ones that used to work.

---

### Post by gruff on 2009-02-07
Thanks David.

> You may have to try an find out what was updated and roll back the packages to the ones that used to work.

Do you know how I would go about doing that?

---

### Post by gruff on 2009-02-07
> You may have to try an find out what was updated and roll back the packages to the ones that used to work. 

Actually, there may be a problem with this - the sound stopped working in Hardy last week and I blindly upgraded to 8.10 thinking that it would solve the problem. Would I need to go back to Hardy Heron?

Sorry for not pointing this out earlier

---

### Post by dcstar on 2009-02-07
> **gruff said:**
> Actually, there may be a problem with this - the sound stopped working in Hardy last week and I blindly upgraded to 8.10 thinking that it would solve the problem. Would I need to go back to Hardy Heron?

Sorry for not pointing this out earlier

If the problem is a configuration issue, then upgrading would not have fixed it.

If you have the disk space (and a separate /home partition), do a fresh install and see if the sound works on that.

---

