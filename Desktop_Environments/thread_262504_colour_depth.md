---
title: "colour depth"
date: 2006-09-21
forum: Desktop Environments
---

### Post by inflik on 2006-09-21
hi i am trying to play a game second life and it is telling me in a log to make sure i am running 32 bit colour depth how would i change that , i tried shearching for it on the forums but failed to do so by the shearch bar

---

### Post by crazedgremlin on 2006-09-21
press ctrl + alt + backspace

press ctrl + alt + f1

type " sudo nano /etc/X11/xorg.conf " (without quotes)

go to Section "Screen"
change "DefaultDepth 24" to "DefaultDepth 32"

:)

---

### Post by inflik on 2006-09-21
thanks man :) yea im still pretty new to linux i dotn know all the ins and outs but i know enough to follow guides and stuff

---

### Post by crazedgremlin on 2006-09-21
Good!  I assume it worked?

---

### Post by crazedgremlin on 2006-09-21
Whoah! Do not do this! I just tried it!  When I said to do it, I was just being dumb.  DO NOT DO IT!   sorry sorry sorry

I'll try to find out how to do it.

---

### Post by crazedgremlin on 2006-09-21
[http://ubuntuforums.org/showthread.php?t=217770&highlight=color+depth](http://ubuntuforums.org/showthread.php?t=217770&highlight=color+depth)

Ok, according to this, 32 bit does not exist!  Wow.
The other 8 channels are Alpha channels.
Um.. I'm confused by the whole error message from Second life now.


Really sorry about my first post. ](*,)

---

### Post by inflik on 2006-09-21
yea it wouldnt let me do it anyways it kept going back to the login screen anyways owell back to installing world of warcraft

---

