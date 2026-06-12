---
title: "Problem with integrated sound card"
date: 2006-06-30
forum: Desktop Environments
---

### Post by HanZo on 2006-06-30
I know there are alreadz some treads open on this subject, but I was able to find some new clues so I thought I'll make a new one.
First of all, I have an Asus A8U-X MoBo with an integrated ADI ad1888 chip (so the manual says). Ubuntu sees it as (quoting from a lspci -v command):
[INDENT]0000:00:04.0 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 810d
        Flags: medium devsel, IRQ 217
        I/O ports at c800 [size=256]
        Memory at fbeff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [40] Power Management version 2[/INDENT]
I found out that it should work with the **snd-intel8x0** driver (in fact under suse it does but I'll get to that later).

the problem is it does not seem to play any sound, the volume icon on the panel spots a nasty red "no-way" icon and if I click on it it says there is no soundcard or some gstreamer plug-ins are missing
in fact when I look in /proc it says there are so soundcards

if I do a lsmod snd it gives me the following result:
[INDENT]root@ubuntu:/home/ubuntu# lsmod |grep snd
snd_intel8x0           33692  0
snd_ac97_codec         92704  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm[/INDENT]

the funny thing is that in suse it works as soon as I enable some options, here is the sound file I have under modprobe.d:
[INDENT]options snd-intel8x0 buggy_irq=1 buggy_semaphore=1 enable=1 index=0

# 8otl.a0P6iRq_lK7:M5455 PCI AC-Link Controller Audio Device
alias snd-card-0 snd-intel8x0[/INDENT]

to me it seems that the buggy_irq and buggy_semaphor flags just solve some irq problems of the motherboard... the problem is I don't know how to do this in ubuntu... any help would be greatly appreciated!

---

