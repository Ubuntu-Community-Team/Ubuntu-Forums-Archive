---
title: "[SOLVED] Ubuntu Installation"
date: 2007-06-06
forum: Dell  Ubuntu Support
---

### Post by For the Birds on 2007-06-06
I'm VERY new to Ubuntu and still trying to install it on my Dell Inspiron E1505.  I used the whole drive to install it and I'm able to get to the point where the system says "take the cd out and reboot".  After the computer reboots I can see Ubuntu starting but then my screen goes dark.  What could be causing that?   I have the resolution set to the lowest available.

---

### Post by meng on 2007-06-06
LCD monitor? I wonder if it's trying to pass too high a refresh rate.
Try ctrl-alt-f1, login and then:
sudo dpkg-reconfigure xserver-xorg
(you can choose defaults for most things, and set refresh rate to 50-60 Hz)

Not sure if this will work (but it shouldn't break anything).

---

### Post by For the Birds on 2007-06-06
Thanks,  I'll give it a try.

---

