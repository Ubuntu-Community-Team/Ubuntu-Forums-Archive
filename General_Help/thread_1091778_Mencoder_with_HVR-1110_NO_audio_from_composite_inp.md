---
title: "Mencoder with HVR-1110: NO audio from composite input"
date: 2009-03-09
forum: General Help
---

### Post by megamania on 2009-03-09
I have a Hauppauge HVR 1110 video card. With this script, I'm able to record tv easily.

```

#!/bin/bash
#(input_type: 0=TV, 1=Composite, 2=SVideo)
input_type=0
filename=myrec.avi

mencoder -tv norm=PAL:chanlist=europe-west:driver=v4l2:width=720:height=576:input=$input_type:fps=25:amode=0:alsa=yes:immediatemode=0:adevice=hw.1,0:audiorate=32000 tv:// -oac copy -ovc lavc -lavcopts vcodec=mpeg4:mbd=1:vbitrate=2400:aspect=4/3 -o $filename -vf crop=700:570:10:0 &

```
If I change the source to composite (input_type=1), however, mencoder only records video, NO audio.
I tried to change the mixer settings of the device (SAA7134). The strange thing is that if I toggle the capture switches (see attached picture), sometimes I get the audio from the card, but only for a few seconds...

I would like to rip some old vhs tapes, and that's the main reason why I bought this card, so I'd really appreciate your help.

---

### Post by megamania on 2009-03-10
On this page:
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1110](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1110)

there's a link to this patch which is supposed to fix the problem:
[http://linuxtv.org/hg/v4l-dvb/rev/40d58d92d183](http://linuxtv.org/hg/v4l-dvb/rev/40d58d92d183)

can somebody please tell me if it's enough to download the file and do a make/make install?

Also, just for my knowledge, is there a way to know when this patch will be included in the package?

thanks a lot.

---

### Post by megamania on 2009-04-07
Just in case anybody is looking for help, the HVR 1110 works fine under 9.04 (Jaunty).

---

