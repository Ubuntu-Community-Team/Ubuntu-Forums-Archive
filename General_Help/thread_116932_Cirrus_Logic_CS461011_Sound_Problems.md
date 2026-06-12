---
title: "Cirrus Logic CS4610/11 Sound Problems"
date: 2006-01-13
forum: General Help
---

### Post by Pneuma on 2006-01-13
In searching for a solution to this problem I've come across a lot of documents dealing with a misrecognition of IBM Thinkpad onboard sound.  The machine I'm running is an old Dell Dimension XPS R350.  I've just installed Ubuntu; there is no sound.

Any thoughts?  All help appeciated.  Thanks!

lspci
0000:00:0b.0 Multimedia audio controller: Cirrus Logic CS 4610/11 [CrystalClear SoundFusion Audio Accelerator] (rev 01)


EDIT:  Woops, please move to Hardware Help.  Thx.

---

### Post by tastefulasever on 2007-07-01
Pneuma, did you ever get this card working.  I have the same machine, same card.  Thanks.

---

### Post by tastefulasever on 2007-07-01
And less than an hour later a solution presents itself.

I found this answer at linuxquestions.org
[http://www.linuxquestions.org/hcl/showproduct.php?product=132&cat=503](http://www.linuxquestions.org/hcl/showproduct.php?product=132&cat=503)

Sound is working now.

I followed the post by hw-tph.

edit /etc/modules.conf

options snd device_mode=0666
alias snd-card-0 snd-cs4236
alias sound-slot-0 snd-cs4236
options snd-cs4236 port=0x530 cport=0x538 isapnp=0 dma1=1 dma2=0 irq=5
# OSS support
alias /dev/mixer snd-mixer-oss
alias /dev/dsp snd-pcm-oss
alias /dev/midi snd-seq-oss

in terminal
sudo /etc/init.d/alsasound start 

and my sound magically kicked on.

---

### Post by LieToPurify3 on 2008-03-10
I'm having this problem with my thinkpad 770z.  I did everything you said, but how is "sudo /etc/init.d/alsasound start" a command? The terminal gives me an error : "command not found"  I'm pretty new to linux, and I havent' had any luck with this Cirrus Logic CS423x

---

