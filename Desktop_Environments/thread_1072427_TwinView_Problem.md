---
title: "TwinView Problem"
date: 2009-02-17
forum: Desktop Environments
---

### Post by Armaron on 2009-02-17
I've just installed Ubuntu 8.10 on my pc and I want to get dual screen support working. But it's not working as intended. At the moment I can't use TwinView (I have an nVidia 9800 GTX2 card, it has 2 GPU's), it's greyed out in the GUI and I can't enable it by manually changing the xorg.conf file. At the moment I'm stuck in a "Seperate X Screen" setup and when I open a program in the second screen, about 80% of the time it crashes the X server.

Can anybody help me get TwinView working?

---

### Post by Armaron on 2009-02-18
Hello, this is a selfwritten, quick response to let you all know that I'm still having the same problem as before. Could anybody help me? Thank you!

---

### Post by Armaron on 2009-02-19
This is the same message as above, but shorter:

Bump!

---

### Post by Armaron on 2009-02-21
Bumpie!

---

### Post by amauk on 2009-02-21
twinview will not work with multiple GPUs
- complain to Nvidia

(I did think that multi-GPU Nvidia cards *could* be used with twinview, but only one GPU was utilised - thereby bypassing the problem at the expense of GPU processing power, but anyway...)

If you want a single screen over 2 monitors with separate outputs, your only option at the moment is Xinerama

Xinerama cannot work with 3D effects
(Xinerama pre-dates graphical hardware acceleration by a long time. it just wasn't designed with hardware acceleration in mind)

Disable the proprietary Nvidia driver, and enable the open 2D driver
Then, using the GUI in preferences > screen resolution, enable multi-desktop

the spec for user level (as opposed to protocol level) GPU sharing is in the works, and will hopefully make RandR 1.3.x
(this will push the issue out of the driver space, and into user level software)

but won't see the light of day for at least a year

---

### Post by Armaron on 2009-02-22
> **amauk said:**
> twinview will not work with multiple GPUs
- complain to Nvidia

(I did think that multi-GPU Nvidia cards *could* be used with twinview, but only one GPU was utilised - thereby bypassing the problem at the expense of GPU processing power, but anyway...)

If you want a single screen over 2 monitors with separate outputs, your only option at the moment is Xinerama

Xinerama cannot work with 3D effects
(Xinerama pre-dates graphical hardware acceleration by a long time. it just wasn't designed with hardware acceleration in mind)

Disable the proprietary Nvidia driver, and enable the open 2D driver
Then, using the GUI in preferences > screen resolution, enable multi-desktop

the spec for user level (as opposed to protocol level) GPU sharing is in the works, and will hopefully make RandR 1.3.x
(this will push the issue out of the driver space, and into user level software)

but won't see the light of day for at least a year

/hug

Thank you my good man for this very informative post. Thank you so much. :)

This may sound noobish, but how do I go about doing that?

---

