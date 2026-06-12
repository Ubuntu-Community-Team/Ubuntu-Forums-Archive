---
title: "Black screen when playing DVD"
date: 2009-03-14
forum: General Help
---

### Post by beejer on 2009-03-14
Hi guys

I have problems getting my DVDs to play. I have installed Mplayer with the Gstreamer backend as well as VLC and both have the same symptom. The players seem to recognize the DVD and start playing it, but it's all a black screen.

I have started VLC from the terminal and get the following messages. 

Can anyone help?

Thx
Bj


VLC media player 0.8.6e Janus

** (.:6256): CRITICAL **: clearlooks_style_draw_focus: assertion `height >= -1' failed
[00000294] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
[00000296] pulse audio output error: Failed to connect to server: Connection refused
[00000296] pulse audio output error: Pulse initialization failed
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
[00000296] jack audio output error: failed to connect to JACK server
[00000296] oss audio output error: cannot open audio device (/dev/dsp)
[00000291] main decoder error: decoder is leaking pictures, resetting the heap
[00000292] main video output error: picture 0xb180fb20 refcount is -1
[00000292] main video output error: picture to date 0xb180f908 has invalid status 6
[00000292] main video output error: picture to display 0xb180f908 has invalid status 6

---

### Post by artheus on 2009-03-14
I believe the error lies in your Graphic-device configuration.

Have you installed the right drivers for your graphical device? so it supports video output?

Cheers

---

