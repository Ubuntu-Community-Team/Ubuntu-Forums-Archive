---
title: "Vostro A860, no sound from headphones"
date: 2012-07-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Litawor on 2012-07-20
I posted this in the  M&A section of the forum, but nobody responded. My laptop is Dell Vostro A860. The sound from speakers works, and it  becomes muted upon plugging headphones as it should. But headphones play  no sound (they're fine though, I checked).

I checked alsamixer and nothing is muted.

As for information that are asked for in similar threads... 
According to lspci command my audio device is: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02).
aplay -l (sorry, it's in Polish, but I guess you know which info is which):
michal@michal-Vostro-A860:~$ aplay -l
**** Lista PLAYBACK urz&#261;dze&#324; ****
karta 0: Intel [HDA Intel], urz&#261;dzenie 0: CONEXANT Analog [CONEXANT Analog]
  Urz&#261;dzenia podrz&#281;dne: 1/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0
karta 0: Intel [HDA Intel], urz&#261;dzenie 1: Conexant Digital [Conexant Digital]
  Urz&#261;dzenia podrz&#281;dne: 1/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0

Can anyone help me? Do I need to provide additional information? I'm not  experienced in this, so I need step-by-step instructions.

By the way, this problem appeared suddenly after rebooting the system  today. The sound in headphones disappeared along with my wallpaper! Is  there any explanation for this?

---

### Post by Vakman on 2012-07-21
Open "Sound Settings". Under "Mode", while your headphones are selected, change it to Analog Speakers if that is an option.

---

### Post by Simplicius on 2012-08-17
> **Thisislaw said:**
> Open "Sound Settings". Under "Mode", while your headphones are selected, change it to Analog Speakers if that is an option.

I have the exact same problem as the original poster. Weird part is that in "Sound Settings" the "Mode" is there only when headphones aren't plugged in. Basically, the moment I plug them in, "Mode" disappears. Ideas?

---

