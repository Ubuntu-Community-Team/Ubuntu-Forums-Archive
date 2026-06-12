---
title: "How to change login screen background in  Ubuntu 13.04?"
date: 2013-05-02
forum: Desktop Environments
---

### Post by NBPX on 2013-05-02
I don't like colonoscopy images. Is there some directory where login screen background is stored?

---

### Post by grahammechanical on 2013-05-03
The image that you are referring to is called warty-final-ubuntu.png. Although this image changes slightly from release to release its name stays the same. I guess if you want and if you have another image of a similar size and type you could call it warty-final-ubuntu and use it to replace the image that is there.

Oh, you want the directory, usr/share/backgrounds/ They are all there.

If you really want to go poking around, then the display manager for the login screen is called lightdm and the greeter-session is unity-greeter. Find that location and you can mess around with the login screen logos. I won't tell you where to find it as that will spoil your fun. :) Mustn't make it too easy for you. Ennit.

Regards

---

### Post by muppet317 on 2013-05-05
Handy intro to lightdm including how to change the login wallpaper here [https://wiki.ubuntu.com/LightDM#Change_the_wallpaper](https://wiki.ubuntu.com/LightDM#Change_the_wallpaper)

---

