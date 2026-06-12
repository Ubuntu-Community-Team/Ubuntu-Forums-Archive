---
title: "Bad Sound"
date: 2005-08-05
forum: Desktop Environments
---

### Post by theFallen on 2005-08-05
Hi,

Again someone totally new to Linux. :D

I really have bad sound coming out of my speakers. Its like hearing sound out of tin cans :( 
I must say, it was not like this in the beginning. I am not sure, but I think it started after installing xine.
Well after I searched in Google and this Forum, I disabled esd and installed ALSA. (I used the hints given in one thread) Here some commands and their results:

 cat /proc/asound/cards 
0 [V8235          ]: VIA8233 - VIA 8235
                     VIA 8235 with ALC650F at 0xe000, irq 22

lspci | grep -i audio 
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)

(This one is a bit astounding, because I have a TV Card installed, which is shown in system -> systemproperties -> hardware (translated from german so may not be correct). Why is it not shown in the bash?)

I also installed all codecs mentioned in the Ubuntu guide. Could this be the problem?

I also have additionally installed xmms.

I hope there is somenone who can help!

cheers.

---

### Post by yyagol on 2005-08-05
you can try to modify the sound by the alsamixer

```
$alsamixer
``` 
to save the chainges type this
```
$ sudo alsactl store
``` 
let me know if it helps

---

### Post by woedend on 2005-08-05
on my system at least, alsamixer automatically saves any changes so that the latter command was not necessary.  As far as the bad sound...can you describe that?  I noticed mine gets bad if I enable tone control and jack the bass and treble all the way up.  run alsamixer, turn off tone control, and turn PCM down and see if that helps?

---

### Post by theFallen on 2005-08-06
Hi,

thanks yyagol and woedend. It did help. It seems PCM was overmodulated and that's why the sound was so crapy. I turned it down to 77 and it did wonders :D
But I didn't find the switch for Tone Control. At least it doesn't matter anymore :D

And I thought I have to reinstall everything. You saved my day!


thanks and a sunny day,
theFallen

---

### Post by woedend on 2005-08-06
no problem.  Not all soundcards have tone control.  If you do, It would be the second one over, it just says Tone.  If it has a green block in it, highlight it then push M to remove it.  Another trick I found that I like better is turning down the value 'Front' instead of PCM.  It's not PCM-Front, just Front.  It has the same effect as PCM, but this way I can adjust the PCM as loud as I want(this is what XMMS and Totem, etc change when adjusting volume) without the distortion.  So try jacking the master up, the front down to 80 or so, and the PCM should not effect the quality.

---

### Post by varunus on 2005-08-06
If you want to get ESD back, you can now, but follow this howto first:  
[http://www.ubuntuguide.org/#configuresoundproperly](http://www.ubuntuguide.org/#configuresoundproperly)

However, skip the step where you disable gnome sounds and the sound server.  After following that howto, ESD and ALSA can coexist, so there's no need to turn off GNOME sounds.

---

### Post by theFallen on 2005-08-07
@varunus
I already did it. I think I went through the whole UserGuide :D

@woedend
There is nothing like Front and neither PCM-Front  :-?

---

