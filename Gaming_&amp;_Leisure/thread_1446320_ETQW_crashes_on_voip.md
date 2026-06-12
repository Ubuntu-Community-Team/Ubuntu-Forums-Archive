---
title: "ETQW crashes on voip"
date: 2010-04-03
forum: Gaming &amp; Leisure
---

### Post by Vadi on 2010-04-03
Has anyone run into quake wars crashing when you try to use voip to talk? I searched about and didn't really find a problem.

Using ETQW 1.5, on Ubuntu KK 64bit. Pulseaudio as audio system.

---

### Post by Vadi on 2010-04-04
Any ideas?

---

### Post by wscott on 2010-04-12
same here. :-(

---

### Post by deadmnky on 2010-04-13
The only way I have been able to use voip is to disable pulse or remove it entirely.

here is a link to remove pulse 

[http://ubuntuforums.org/showthread.php?t=1313253&highlight=remove+pulse+audio](http://ubuntuforums.org/showthread.php?t=1313253&highlight=remove+pulse+audio)

I believe to suspend pulse while you play the command would be

> pasuspend ./YOUR/DIRECORY/TO/ETQW/etqw
add -rthread to after etqw for multi processor support. 
hope it all works out for you

---

### Post by MichiganMan on 2010-06-19
The reason for the crashes is that your mic hasn't been correctly identified in .etqwcl/base/etqwconfig.cfg.  If nothing is there (the default) then the game crashes when you try to use voip.

Open etqwconfig.cfg and look for "seta s_micDevice "  and "seta s_alsa_mic"  (Actually I think only the second one matters but I set them both)  I forget the terminal command that revealed this to me (long ago) but my usb mic is plughw:1.  I believe my sound card is plughw:0.   So the lines in my etqwconfig.cfg read:

> seta s_micDevice "plughw:1"

> seta s_alsa_mic "plughw:1"

Obviously I only have a tenuous grasp on why this works and hopefully someone more knowledgeable can step in and offer more details (like reminding me how I discovered what the identifier for my mic was) , but I've struggled with VOIP crashing ETQW and can tell you that its most likely because the mic isn't correctly identified in etqwconfig.cfg

---

### Post by Vadi on 2010-06-20
Thanks, I'll give it a try next time I play.

---

### Post by J.K.Makowka on 2010-06-20
The 30 sec sound delay with pulseaudio and ETQW doesn't happen KK? Hmmm maybe I should have not upgraded to LL then :(

---

