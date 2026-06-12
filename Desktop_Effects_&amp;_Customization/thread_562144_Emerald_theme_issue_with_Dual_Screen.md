---
title: "Emerald theme issue with Dual Screen"
date: 2007-09-28
forum: Desktop Effects &amp; Customization
---

### Post by oderus on 2007-09-28
I have Compiz-Fusion 0.5.2 running on Gutsy Alpha 5 on a Dell D620 with Nvidia propriety drivers (v100.x). I have dual monitors setup as separate screens and Compiz-Fusion is working on both screens as expected. Cube works, effects work etc etc. Primary is my Dell LCD laptop screen and the secondary screen is a Dell 19" LCD.

What doesn't work properly is Emerald. It will only apply to one screen (my laptop display) and the other shows no borders. I can temporarily fix it by running "emerald --replace" via ALT-F2 from the second screen, not the first screen and it works. I want to have this running on bootup without the extra input. I'm not sure how to add this to sessions so it applies to the second screen.

Anyone?

Thanks in advance.

---

### Post by gregbazar on 2007-09-28
I have the same issue.

Sony VIAO Laptop, with 13" monitor, and 24" attached to the external port, on the NVIDIA card.

Everything works, but emerald doesn't start on the 13" monitor, which is set to screen 1, and the 24" is set to screen 0.

If I mouse on over to the 13" Screen 1 and type emerald --replace, BAMM! works great.

How can I get emerald to fire up on a certain display?  Does it read the DISPLAY env variable?  It doesn't have a --display option like compiz does......

Thanks for the help in advance.

Greg

---

### Post by olavjunior on 2008-01-27
I'm wondering about the exact same ting! How did you solve it?

---

### Post by kryth on 2008-01-27
This worked for me.

#!/bin/bash
sleep 2
DISPLAY=":0.0" /usr/bin/compiz --replace ccp --sm-disable --only-current-screen &
DISPLAY=":0.1" /usr/bin/compiz --replace ccp --sm-disable --only-current-screen &
DISPLAY=":0.0" /usr/bin/emerald --replace &
DISPLAY=":0.1" /usr/bin/emerald --replace &

just copy and paste it into a terminal if it works, then you can make it a script that starts on startup.  I don't remember how to do that....something to do with chmod +x 777....or something like that. I'm sure someone smart can tell ya.

---

