---
title: "UBUNTU 9.10: How do I fix the black screen?"
date: 2009-11-07
forum: Gaming &amp; Leisure
---

### Post by jackpotmoney on 2009-11-07
Everytime I try to start up Mupen64PLUS, it loads the game and says something about the game starting, then the screen goes black.

The same thing happens with TuxCube.
When I start it up, it goes to a black screen and then I have to close out the black screen.


Stuff like this worked just fine with windows vista.

I moved from Vista to Ubunut because of speed issues.

Any help thanks!:p

---

### Post by handy on 2009-11-07
Could you post the results of entering the following in the Terminal:

glxinfo |grep -i opengl

---

### Post by nexoncore on 2009-11-08
Its not by any chance the program freezing, I have noticed that in 9.10 that alot of programs freeze under low stress.

---

### Post by jackpotmoney on 2009-11-08
> **handy said:**
> Could you post the results of entering the following in the Terminal:[PHP]
[/PHP]
glxinfo |grep -i opengl

anthony@Laptop:~$ glxinfo |grep -i opengl
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 (RS400 5975) 20090101 x86/MMX+/3DNow!+/SSE2 NO-TCL
OpenGL version string: 1.5 Mesa 7.6
OpenGL extensions:
anthony@Laptop:~$

---

### Post by handy on 2009-11-09
Unfortunately your AMD/ATi dropped support for your GPU:

[http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy&num=1)

The open-source support is currently moving very fast, but for you as a new Linux user to be able to take advantage of the cutting edge software, which would give you the best 3D results, (though still not optimal) is not really a good idea.

If you are interested you could have a look at this thread, at the bottom of the first post there are some links which will expand your understanding, but they won't solve your problem I'm sorry to say.

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

You card will get good open-source support, I dare say sometime inside of the next 12 months, best I can do for you sorry. :-|

---

