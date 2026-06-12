---
title: "Compiz Xgl ? Question !!!"
date: 2006-04-10
forum: Desktop Environments
---

### Post by p47 on 2006-04-10
Hello everybody I hope somebody can help me because I got Some problems with xgl and compiz.

Now I have compiz and xgl run, but sometimes is very slow !
When I wan to open firefox, firefox open slow and before to install compiz and xgl I dont have problems with limewire and amsn now when I wan to epen amsn or limewire the computer never open thah programs...
Why?

My second Qustion is that before that intall compiz and xgl when I typed glxgears that looks very good, now is slow that animation, and in glrxinfo I can see direct rendering: No

I have this when I type glxgears

16465 frames in 5.0 seconds = 3274.111 FPS
12882 frames in 5.0 seconds = 2564.648 FPS
17480 frames in 5.0 seconds = 3494.274 FPS
17670 frames in 5.0 seconds = 3521.107 FPS
17688 frames in 5.0 seconds = 3521.874 FPS
17670 frames in 5.0 seconds = 3521.927 FPS
17687 frames in 5.0 seconds = 3522.510 FPS
17328 frames in 5.0 seconds = 3454.900 FPS
17573 frames in 5.0 seconds = 3497.523 FPS
17556 frames in 5.0 seconds = 3485.794 FPS
17545 frames in 5.0 seconds = 3508.999 FPS

Is it normal ? in these commands ?
Help me please !
Regards.

---

### Post by AndrewJ on 2006-04-11
As I recall 3D applications and games suffer from XGL (remember you disabled DRI - Direct Rendering in your xorg.conf to get XGL working).

As far as I know this is an issue with drivers and should (hopefully) be resolved in the near future. Until then you might have to disable XGL and re-enable DRI for daily activity.

Fortunately XGL is updating at a rapid pace :)

---

### Post by p47 on 2006-04-11
Now I've compiz and XGL and all is very good, but I got some problems, I can not open limewire and amsn ?
Do you know Why ?

---

