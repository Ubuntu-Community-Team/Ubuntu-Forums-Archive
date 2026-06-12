---
title: "skype: twitching sound"
date: 2005-04-12
forum: Desktop Environments
---

### Post by Zlatan on 2005-04-12
looks like buffer or driver problem- definitely not connection speed problem...
what problem could it be?

---

### Post by stevenyu on 2005-04-12
I also have some roboti/delay sound delaying issue when i talk to my friend in skype for linux, i test my windows version there is no issues at all, seems to be some kind of buffer issues.

---

### Post by syltty on 2005-04-13
This helped me with crappy sound quality with skype:

sudo -s
echo "skype 256 65535 direct block" > /proc/asound/card0/pcm0p/oss
echo "skype 256 65535 direct block" > /proc/asound/card0/pcm0c/oss
exit

---

### Post by Zlatan on 2005-04-14
sorry- did not help


[QUOTE=syltty]This helped me with crappy sound quality with skype:

sudo -s
echo "skype 256 65535 direct block" > /proc/asound/card0/pcm0p/oss
echo "skype 256 65535 direct block" > /proc/asound/card0/pcm0c/oss
exit[/QUOTE]

---

