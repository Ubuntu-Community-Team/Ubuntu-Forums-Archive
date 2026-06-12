---
title: "Dell Precision 690 workstation - no sound"
date: 2008-11-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by uts on 2008-11-08
Hi,

Can anyone tell what value should I set for the "model" parameter to get sound working in Dell Precision 690 workstation?

"lspci |grep Audio" shows 

00:1b.0 Audio device: Intel Corporation 631xESB/632xESB High Definition Audio Co
ntroller (rev 09)

"alsa-config" detects the card and writes 
"/etc/modprob.d/sound" as

alias snd-card-0 snd-hda-intel
options snd-hda-intel index=0

Testing with "aplay /usr/share/sound/phone.wav" produces no sound. Mixer is *un-muted*.

In fact, I've tried various values of model=xxx listed here
[http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)
and none seemed to work.

My kernel version is 2.6.26-1-amd64, alsa version is 1.0.17.

Thanks in advance,
uts
--

---

### Post by Gisli Ottarsson on 2009-01-23
Were you able to find a solution to this problem?  If so, please share.

---

### Post by uts on 2009-01-24
No, unfortunately. :-(

---

### Post by lalamax3d on 2009-07-23
any usb based sound card option available in market...

i tried finding drivers in dell, linux section. there are almost for everything except sound

any ideas. please do share

---

### Post by daklein on 2011-01-14
it works now out of box, on my ebay special Dell 690, what a heavy machine, oh yeah!      using ubuntu 10.10 x64       :D     Well, after plugging into the audio output jack, instead of line in.....](*,)

---

