---
title: "[Kubuntu] Artsd loaded, alsa not muted; no sound"
date: 2005-08-15
forum: Desktop Environments
---

### Post by zAo on 2005-08-15
Hello all,

I used ubuntu for some months now; everything was great. I only wanted KDE as my DE, so I installed kde. After some problems I decided to reinstall kubuntu, no I only have no sound!

This is my soundcard:
```
0000:00:0d.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
``` 

The modules are loaded:
```
$ lsmod | grep cs46
snd_cs46xx             86664  3
snd_rawmidi            24928  1 snd_cs46xx
snd_ac97_codec         74208  1 snd_cs46xx
snd_pcm                94920  5 snd_cs46xx,snd_ac97_codec,snd_pcm_oss
snd                    55268  12 snd_cs46xx,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc          9796  2 snd_cs46xx,snd_pcm
gameport                4544  1 snd_cs46xx
``` 

Artsd is running:
```
$ ps -ef | grep arts
zao       7783  7497  1 12:32 ?        00:00:05 /usr/bin/artsd -F 10 -S 4096 -a alsa -d -s 60 -m artsmessage -c drkonqi -l 3 -f
``` 

And my alsamixer is not muted (how can I show you that?)

Every MP3 player plays my files, without any errors:
```
$ mpg123 Chevelle\ -\ Point\ #1\ -\ 01\ -\ Open.mp3
High Performance MPEG 1.0/2.0/2.5 Audio Player for Layer 1, 2, and 3.
Version 0.59q (2002/03/23). Written and copyrights by Joe Drew.
Uses code from various people. See 'README' for more!
THIS SOFTWARE COMES WITH ABSOLUTELY NO WARRANTY! USE AT YOUR OWN RISK!
Title  : Open                            Artist: Chevelle
Album  : Point #1                        Year  : 1999
Comment: Defender Lame 3.90.3 aps        Genre : Metal

Playing MPEG stream from Chevelle - Point #1 - 01 - Open.mp3 ...
MPEG 1.0 layer III, 128 kbit/s, 44100 Hz joint-stereo
```


In Gnome everything worked out-of-the-box, now on a clean Kubuntu, it doesnt work.

Who can help me?

Thanks in advance!

---

### Post by zAo on 2005-08-15
Finally; found it!

Quote from [here](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=339942&highlight=cs46xx) 
> I had a similar problem with my Sound Fusion CS46XX card. I observed that the "ADC" and "DAC" in the "Input" tab of kMix were set to 0. I increased the values of these and I get the sound now. Note that this may have to be done separately as each user in kMix. Doing this only in root will do it only for root.

---

