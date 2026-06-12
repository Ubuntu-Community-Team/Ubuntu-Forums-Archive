---
title: "How? control volumn independently"
date: 2005-06-14
forum: Desktop Environments
---

### Post by oasiscity on 2005-06-14
I open realplayer and rythmbox.
they work at the same time.

but, it seems that realplayer is the "master" of the volumn overall
if I change the volumn in realplayer, then the volumn changes accordingly in rythmbox.
if I change it rythmbox, realplay's volumn remains the same.

I can live with this, but just try to know more about sound stuff.
Is there a way to make APP control its own volumn only?

I read the sound HOWTO, can't understand fully.
-------------------------------------------------------------
I use Gstreamer, and the output sink is ALSA.

zwf@ubuntu:~$ lsof /dev/snd/*
COMMAND    PID USER   FD   TYPE DEVICE SIZE NODE NAME
rhythmbox 8752  zwf  mem    CHR 116,16      7768 /dev/snd/pcmC0D0p
rhythmbox 8752  zwf   27u   CHR 116,16      7768 /dev/snd/pcmC0D0p
zwf@ubuntu:~$ lsof /dev/dsp
COMMAND    PID USER   FD   TYPE DEVICE SIZE NODE NAME
esd       8643  zwf    5w   CHR   14,3      7758 /dev/dsp
realplay. 8895  zwf    5w   CHR   14,3      7758 /dev/dsp

---

