---
title: "EnemyTerritory Sound Problem"
date: 2007-07-18
forum: Gaming &amp; Leisure
---

### Post by XRGB48 on 2007-07-18
I have an ASRock motherboard with the onboard sound chip C-Media CM6501 that is identified as an USB sound card in FeistyFawn. At first I had no sound at all. Then I run "asoundconf set-default-card default" and now I have sound in Ubuntu. The question is how do I get EnemyTerritory to use the USB sound card?

---

### Post by XRGB48 on 2007-07-18
I get this error in the console
------- sound initialization -------
/dev/dsp: No such file or directory
Could not open /dev/dsp

I thought this would help but it makes no difference 
sudo su
echo "et.x86 0 0 direct" > /proc/asound/default/pcm0p/oss

---

