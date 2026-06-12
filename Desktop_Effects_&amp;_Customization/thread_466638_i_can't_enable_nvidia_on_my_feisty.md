---
title: "i can't enable nvidia on my feisty"
date: 2007-06-06
forum: Desktop Effects &amp; Customization
---

### Post by jvanoort05 on 2007-06-06
i just installed feisty on my dell inspiron 8100 and when i try to enable desktop efects a msg box tells me to enable nvidia. i hit enable and i tells me to rebbot and when i reboot it is not enabled. what am i doing wrong?????

---

### Post by Nythain on 2007-06-07
in terminal type
sudo apt-get install nvidia-glx
(for the 9631 drivers)
or
sudo apt-get install nvidia-glx-new
(for the 9755 drivers)
to install the proprietary drivers
then
gksudo nvidia-settings
to set up the xorg.conf file
then reboot or just restart xserver with control alt backspace
and last, try turning back on desktop effects

hope that gets things going for you

---

### Post by jvanoort05 on 2007-06-07
ok i will try that but first how do i tell which driver i am using? sorry for all the questions but i am new to ubutnu.

---

### Post by Nythain on 2007-06-07
cards within the last year or so could use the 9755, if its a few years old, i would stick with the 9631... and if its really really old (like tnt2 ish) then legacy is the one for your... more than likely you can get away with nvidia-glx-new

---

