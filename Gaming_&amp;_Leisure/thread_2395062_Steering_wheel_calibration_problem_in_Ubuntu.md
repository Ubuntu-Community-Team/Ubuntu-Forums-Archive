---
title: "Steering wheel calibration problem in Ubuntu"
date: 2018-06-26
forum: Gaming &amp; Leisure
---

### Post by haider04 on 2018-06-26
Hi guyz,

I am trying to use a Leobodnar Simsteering FFB steering wheel in Linux Ubuntu LTS 16.04.4 OS but the problem is whenever i rotate the wheel to some degrees from its center (both left, right), i am unable to see any change in values by using this command "jstest /dev/input/js1". But after some degrees of rotation, say 20 degrees, only then i can see the values changing and see the wheel working. Anyhow, my Fanatec pedals (throttle, brake) are working fine. I installed the following package to make things working:


[LIST]
[*]$apt-get install ros-kinetic-joystick-drivers
[/LIST]

The same thing is depicted whenever i use the wheel in car simulations. (i removed deadzone from there). There is somehow a dead zone applied around its center in Linux and i don't know how to fix it. Nevertheless, it works completely fine in windows.

I tried using jscalibrator for wheel calibration but i think this package don't exist anymore. I also saw this thread ([https://ubuntuforums.org/showthread.php?t=480264](https://ubuntuforums.org/showthread.php?t=480264)) in which the problem was resolved by this package, but that's long ago. And latest Linux environments don't support jscalibrator anymore. 

I wanted to ask if some other person has also encountered same situation? How this calibration problem could be resolved in Linux? I am stuck in it for so many days but no luck so far.

Are there any other solutions available for this? Please let me know and share your experiences. 

Any leads would be helpful. Thanks! 

Regards,
Haider

---

