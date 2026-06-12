---
title: "MIDI keyboard problems on 5.10 i386"
date: 2006-01-07
forum: General Help
---

### Post by Max Hadley on 2006-01-07
I am having problems trying to get any application other than amidi to recognise my midi keyboard. amidi sees the keyboard and receives messages from it just fine:
[INDENT]$amidi -l
Device    Name
hw:0,0    ES1371

$amidi -d -p hw:0,0

90 3E 64
   3E 00
   3E 64
   3E 00
90 3C 64
   3C 00
14 bytes read

[/INDENT]
Rosegarden doesn't see the midi input at all, neither does zynaddsubfx. I also can't generate any sound output, but I don't think the sound card has a hardware synthesiser:
[INDENT]cat /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.9 emulation code)
Kernel: Linux valpc 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
Ensoniq AudioPCI ENS1371 at 0x1080, irq 17

Audio devices:
0: ES1371 DAC2/ADC (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices:
0: ES1371

Timers:
7: system timer

Mixers:
0: Cirrus Logic CS4297A rev 3
[/INDENT]
The midi-specific modules loaded are:
[INDENT]$ lsmod | grep midi
snd_rawmidi            22816  1 snd_ens1371
snd_seq_device          8204  1 snd_rawmidi
snd                    48644  10 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
[/INDENT]
When I open Rosegarden's sequencer, it gives me warning messages complaining about a non-existent /dev/sequencer. That might explain the lack of sound output. However, in midi setup, there is no record device available, and I cannot type in the edit box: The 'Device' is set to /dev/null, & typing in /dev/midi (or indeed, anything else at all) gives a 'device invalid or busy' message.

How do I go about:

1. Getting Rosegarden (or anything other than amidi) to recognise the keyboard?
2. Getting sound out of Rosegarden (zynaddsubfx makes sounds OK, but doesn't see the keyboard either)

I have searched around some other threads, but I can't find answers to this particular set of problems,

Thanks

Max

---

