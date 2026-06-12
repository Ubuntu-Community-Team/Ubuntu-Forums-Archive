---
title: "Dell Inspiron M5010 and ubuntu 3D"
date: 2012-09-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jolubaes on 2012-09-12
Well,  I just bought this computer with a video card Ati Radeon HD4250, I installed ubuntu 12.04 and when I the OS starts it just freeze, the only thing that I can do is to move the cursor, but nothing else work. In the other hand, if I start in 2D mode it works fine (without any 3D option of course).

This is what I have tried so far without succes:

1. I have tried the "ATI/AMD  proprietary FGLRX grapics driver" in the additional drivers section

2. I also have tried the "ATI/AMD  proprietary FGLRX grapics driver (post-release updates)" in the additional driver section

3. I also installed the driver provided by AMD... catalysits 12.4 and the newest catalyst 12.6
[http://askubuntu.com/questions/129597/how-do-i-fix-my-installation-of-ati-catalyst-video-drivers-in-12-04-lts](http://askubuntu.com/questions/129597/how-do-i-fix-my-installation-of-ati-catalyst-video-drivers-in-12-04-lts)
[http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers](http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers)

So far is the same result... no 3D options working

Any suggestion???

---

### Post by 2F4U on 2012-09-13
Did you verify that your graphics card can run Unity in 3d?

In a terminal run

/usr/lib/nux/unity_support_test -p 

It should test the capabilities of your machine and its ability to run Unity in 3D. 

[http://askubuntu.com/questions/128149/why-cant-i-use-unity-3d-in-ubuntu-12-04](http://askubuntu.com/questions/128149/why-cant-i-use-unity-3d-in-ubuntu-12-04)

---

### Post by jolubaes on 2012-10-07
thanks for the advice. I did what you suggested and all lines are mark with a YES, including this one

Unity 3D supported:       yes

 so I believe is something else. Any other idea?

---

