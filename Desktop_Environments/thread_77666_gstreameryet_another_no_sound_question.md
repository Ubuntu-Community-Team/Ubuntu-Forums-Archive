---
title: "gstreamer/yet another no sound question"
date: 2005-10-17
forum: Desktop Environments
---

### Post by krcm on 2005-10-17
Hi,
I've installed kubuntu a few days ago and have not had any sound since.
I've been searching the forum and have tried lots of things but no luck so far.

[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)
I followed this link en tried to instal, but i always get the message that the package can't be found.

I have tried to download the package but there are so many different gstreamer0.8'x' packages that I didn't know wich 'x' to choose.


here is some more information:

COMMAND  PID USER   FD   TYPE DEVICE SIZE NODE NAME
artsd   6956   an  mem    CHR 116,16      7775 /dev/snd/pcmC0D0p
artsd   6956   an   12u   CHR 116,16      7775 /dev/snd/pcmC0D0p
artsd   6956   an   13r   CHR 116,33      7533 /dev/snd/timer
kmix    6971   an   10u   CHR  116,0      7476 /dev/snd/controlC0
artsd   7047   an  mem    CHR 116,16      7775 /dev/snd/pcmC0D0p
artsd   7047   an   12u   CHR 116,16      7775 /dev/snd/pcmC0D0p

and another one from today, the above info is from yesterday, a few things have changed:
an@racinger:~$ killall esd
an@racinger:~$ lsof /dev/dsp
an@racinger:~$ lsof /dev/snd/*
COMMAND  PID USER   FD   TYPE DEVICE SIZE NODE NAME
artsd   6981   an  mem    CHR 116,16      7800 /dev/snd/pcmC0D0p
artsd   6981   an   11u   CHR 116,16      7800 /dev/snd/pcmC0D0p
artsd   6981   an   21r   CHR 116,33      7532 /dev/snd/timer
kmix    6999   an   10u   CHR  116,0      7524 /dev/snd/controlC0
artsd   7404   an  mem    CHR 116,16      7800 /dev/snd/pcmC0D0p
artsd   7404   an   11u   CHR 116,16      7800 /dev/snd/pcmC0D0p


lsmod|grep snd
snd_intel8x0           29984  3
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  0
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  2 snd_pcm
snd                    50276  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  1 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm


[http://www.ubuntuguide.org/#configuresoundproperly](http://www.ubuntuguide.org/#configuresoundproperly)  
this link got me nowhere either.

Hopefully somebody here can help me.
Thx for trying anyway
An

---

### Post by krcm on 2005-10-19
Maybe this information will also help


an@racinger:~$ lsof /dev/snd/*
COMMAND  PID USER   FD   TYPE DEVICE SIZE NODE NAME
artsd   6970   an  mem    CHR 116,16      7830 /dev/snd/pcmC0D0p
artsd   6970   an   11u   CHR 116,16      7830 /dev/snd/pcmC0D0p
artsd   6970   an   13r   CHR 116,33      7508 /dev/snd/timer
kmix    6988   an   10u   CHR  116,0      7493 /dev/snd/controlC0
artsd   7940   an  mem    CHR 116,16      7830 /dev/snd/pcmC0D0p
artsd   7940   an   11u   CHR 116,16      7830 /dev/snd/pcmC0D0p

thx for looking
An

---

