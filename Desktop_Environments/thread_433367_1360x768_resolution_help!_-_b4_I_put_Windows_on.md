---
title: "1360x768 resolution help! - b4 I put Windows on"
date: 2007-05-04
forum: Desktop Environments
---

### Post by rickrude on 2007-05-04
Hello,

I am a fan of ubuntu and have it running on an ibm z60 which is perfect.

I have bought myself a Samsung LA40S71BX LCD TV capable of 1360x768, but can only get 640x480 - doesn't make a good mythTV box.

Anways, I have a Dell GX270 with an NVidia MX440 with DVI plugged in through HDMI of TV, which I am hoping to run mythTV.

As well as that there is overscan - even more with the new nvidia drivers that I installed by following [this guide]("http://doc.gwos.org/index.php/Latest_Nvidia_Edgy").

Any change that I make in xorg.conf, it doesn't flinch and just happilly displays 640x480. i will end up putting my boot through it, or worse, installing Windows xp - which displays 1366x768 perfectly.

Does anyone know what I can do to get the correct resolution and display size? I have searched and tried suggested modelines and display sizes.

Thanks for reading!



rick.

---

### Post by abc123456 on 2007-05-04
Try dropping xorg.conf from 24 bit to 16 bit.  Some of the higher res use lower DefaultDepth of 16 vs DefaultDepth 24.  on my machine DefaultDepth 24 gives 1600x1200 where as DefaultDepth 16 gives 1920x1440.

---

### Post by rickrude on 2007-05-04
Good suggestion, but still 640x480.. thanks

---

### Post by rickrude on 2007-05-05
I have it running now at 1280x720 with a bit of overscan. All I did was changed "1360x768" to "1280x720" under default depth 24 after reading some article about 720p.

---

