---
title: "Lost my alsa device?"
date: 2006-01-14
forum: Desktop Environments
---

### Post by syklitengutt on 2006-01-14
Hi.
Installed xubuntu yeasterday, and today at startup I cant play any sounds.
If I in Xfce goes into Xfce Mixer settings I cant choose any device?

It worked fine under xfce yeasterda...
Its missing from gnome also???

---

### Post by syklitengutt on 2006-01-14
If I go into synaptic and check its still installed...
alsa-base and alsamixergui

---

### Post by syklitengutt on 2006-01-14
heres an update.
If I type alsamixer in konsole I get this message:
alsamixer: function snd_ctl_open failed for default: No such file or directory

---

### Post by syklitengutt on 2006-01-14
and another:
chris@chris:~$ aplay -l
aplay: device_list:218: no soundcards found

wtf.... It worked fine until yeasterday???
Why should my soundcard just dissapear?

---

### Post by syklitengutt on 2006-01-14
and anotherone....
heres what lspci -v gives me about the soundcard:
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8
237 AC97 Audio Controller (rev 50)
        Subsystem: Asustek Computer, Inc. A7V600 motherboard (ADI AD1980 codec [
SoundMAX])
        Flags: medium devsel, IRQ 5
        I/O ports at e000 [size=256]
        Capabilities: <available only to root>

---

### Post by syklitengutt on 2006-01-14
ok....
I also installed the InitNG boot thingy. If I boot the regular way I get my sound.
So for what I can think of the InitNG have disabled the sound loading....
How to fix this?

---

### Post by inhuman!!! on 2006-04-09
I have the same problem!!!
But i have played with "sysv-rc-conf", and after that there is no sound!

---

### Post by Ramses de Norre on 2006-04-09
Try to enable some of the services you disabled, some of them will affect your sound.

---

### Post by inhuman!!! on 2006-04-09
I have tried them all, but no result.
there is no /dev/dsp . which module does initialize the soundcard?

---

### Post by inhuman!!! on 2006-04-10
I fixed the problem. I shoud've loaded the intel8x0 module for my sound card.

---

### Post by Googler on 2006-05-13
how did you load intel8x0 module ?

---

