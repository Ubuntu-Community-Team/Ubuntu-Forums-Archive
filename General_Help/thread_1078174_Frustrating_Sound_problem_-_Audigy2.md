---
title: "Frustrating Sound problem - Audigy2"
date: 2009-02-23
forum: General Help
---

### Post by Chrus on 2009-02-23
Hi

So heres the thing... im having a real hard time getting sound to work in ubuntu. Been doing a lot of googleing, with mixed results. I managed to get sound working at one point, although it wouldnt work in all apps and the volume was kinda low. So i did a bit more tinkering today and now i have no sound at all. Ive given up on google... thought it was time i posted here to get an answer for my specific problem.

Im running ubuntu 8.10(should prob mention its the x64 ver). sound card is an Audigy2 (my mobo has onboard sound, but i dont want to use that one). Ive also got 5.1 speakers, so it would be nice to have sound coming out all of them. Gonna dump a heap of stuff that i think might be usefull...

lspci | grep -i audio
```
00:0e.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
02:06.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
```

lsmod | grep snd
```
snd_emu10k1_synth      15616  0 
snd_emux_synth         46720  1 snd_emu10k1_synth
snd_seq_virmidi        14592  1 snd_emux_synth
snd_seq_midi_emul      16128  1 snd_emux_synth
snd_emu10k1           164128  5 snd_emu10k1_synth
snd_hda_intel         492336  2 
snd_ac97_codec        133080  1 snd_emu10k1
ac97_bus               10368  1 snd_ac97_codec
snd_pcm_oss            52608  0 
snd_mixer_oss          25088  2 snd_pcm_oss
snd_seq_dummy          11524  0 
snd_pcm                99208  4 snd_emu10k1,snd_hda_intel,snd_ac97_codec,snd_pcm_oss
snd_seq_oss            42368  0 
snd_seq_midi           15872  0 
snd_util_mem           13312  2 snd_emux_synth,snd_emu10k1
snd_hwdep              16904  2 snd_emux_synth,snd_emu10k1
snd_rawmidi            34176  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event     16768  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                67168  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34320  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         16404  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    79432  24 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_hda_intel,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_hwdep,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  2 snd
snd_page_alloc         17680  3 snd_emu10k1,snd_hda_intel,snd_pcm
```

sudo asoundconf list
```
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

Names of available sound cards:
Audigy2
NVidia
```

sudo cat /dev/sndstat
```
Sound Driver:3.8.1a-980706 (ALSA v1.0.17 emulation code)
Kernel: Linux Poseidon 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
Audigy 2 ZS [SB0350] (rev.4, serial:0x20021102) at 0x8c00, irq 16
HDA NVidia at 0xfe020000 irq 20

Audio devices:
0: ADC Capture/Standard PCM Playback (DUPLEX)
1: AD198x Analog (DUPLEX)

Synth devices:
0: Emu10k1

Midi devices:
0: Audigy MPU-401 (UART)

Timers:
31: system timer

Mixers:
0: SigmaTel STAC9750,51
1: Analog Devices AD1988B
```

And ive got ~/.asoundrc (im hopes of getting 5.1 sound
```
pcm.andcard{
type hw
card 0 
device 1
channels 6
}

pcm.dmix6 {
type dmix
ipc_key 1024
ipc_key_add_uid false
ipc_perm 0660
slave {
pcm sndcard
rate 48000
channels 6
period_time 0
period_size 512
buffer_time 0
buffer_size 10240
}
}

pcm.ch51dup {
type route
slave.pcm softvol
slave.channels 6
ttable.0.0 1
ttable.1.1 1
ttable.0.2 1
ttable.1.3 1
ttable.0.4 0.5
ttable.1.4 0.5
ttable.0.5 0.5
ttable.1.5 0.5
}

pcm.softvol {
type softvol
slave {
pcm &#8220;dmix6&#8243;
}
control {
name &#8220;softMaster&#8221;
card 0
count 2
}
}

pcm.duplex {
type asym
playback.pcm &#8220;ch51dup&#8221;
capture.pcm &#8220;hw:0&#8243;
}

pcm.!default {
type plug
slave.pcm &#8220;duplex&#8221;
}
```

If you need any more info let me know and ill be happy to give it.

Any help would be greatly appreciated... im getting super frustrated here.

Cheers

Chrus

---

### Post by Chrus on 2009-02-23
Well a bit more poking around solved most of the problem.

Turns out all i needed to do was in the sounds settings (under switches), turn off "Audigy Analog/Digital Output jack:"

Now I have sound working in all my apps (except VLC, but i assume thats a whole other issue, ill get to that one later).

Still no 5.1 tho. Any ideas on that one? ill keep poking around in the mean time... hopefully i can figure it out.

Cheers

Chrus

---

