---
title: "Enabling MIDI support"
date: 2005-08-27
forum: Desktop Environments
---

### Post by McAviti on 2005-08-27
Hi!

I would like to connect my MIDI keyboard, aber had so far no success with activating my MIDI port. This is the output of /dev/sndstat:
--
Sound Driver:3.8.1a-980706 (ALSA v1.0.6 emulation code)
Kernel: Linux rigatoni 2.6.10-5-386 #1 Thu Aug 18 22:23:56 UTC 2005 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
C-Media PCI CMI8738-MC6 (model 55) at 0x1000, irq 18

Audio devices:
0: C-Media PCI DAC/ADC (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG
[COLOR=DarkRed]
**Midi devices: NOT ENABLED IN CONFIG**[/COLOR]

Timers:
7: system timer

Mixers:
0: CMedia PCI
-- 

When i have a look at the loaded modules, there is a lot of midi related stuff, though:
--
# lsmod |grep midi
snd_seq_virmidi         7296  1 snd_emux_synth
snd_seq_midi_emul       7424  1 snd_emux_synth
snd_seq_midi            8224  0
snd_seq_midi_event      7424  3 snd_seq_virmidi,snd_seq_midi,snd_seq_oss
snd_seq                46992  8 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_oss,snd_seq_midi_event
snd_rawmidi            22944  4 snd_emu10k1,snd_seq_virmidi,snd_seq_midi,snd_mpu401_uart
snd_seq_device          8332  8 snd_emu10k1_synth,snd_emu10k1,snd_emux_synth,snd_seq_midi,snd_seq_oss,snd_seq,snd_opl3_lib,snd_rawmidi
snd                    50276  18 snd_emu10k1,snd_ac97_codec,snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
--

I think the problem is the line 'Midi devices: NOT ENABLED IN CONFIG' - but what is the cure?  :| 

Thanks for any advice,
klemens

---

### Post by panki on 2007-01-09
did you ever get this to work?

---

