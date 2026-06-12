---
title: "Kubuntu 7.10 + ATI = KDE ARTIFACT ?"
date: 2007-11-05
forum: Desktop Environments
---

### Post by krak on 2007-11-05
hi,
I get some artifact at right bottom corner look at picture [http://img126.imageshack.us/img126/6339/fotodw1.jpg](http://img126.imageshack.us/img126/6339/fotodw1.jpg) i had to take photo when i make a screen shoot that artifact is not visible. I found when i shift between desktops eg. (Ctrl + Alt + F6) some times its disappears but after some time its coming back.
How to remove that artifact permanently ? forget to mention that i have Radeon 9600 and using  official drivers (8.42.3) currently latest. 

Thx,

---

### Post by luisromangz on 2007-11-05
It happens to me too, and I am using the same drivers as you, although I have a 200M video card. It only happens when I run KWin, not when using Compiz (which I do almost all the time, now that the new drivers brought support for AIGLX).

---

### Post by TeaSwigger on 2007-11-05
That'd be "artifaKt" :)

Honestly I don't know much about this but perhaps check the /etc/X11/xorg.conf settings. Perhaps specifying monitor settings or some such might help?

Is there a pattern? For instance only if using kicker set to transparent?

Just trying to raise some thoughts.

---

### Post by krak on 2007-11-05
Compiz seems to fix problem but solw down computer :(

---

### Post by loopyloopy on 2007-11-20
> **krak said:**
> hi,
I get some artifact at right bottom corner look at picture [http://img126.imageshack.us/img126/6339/fotodw1.jpg](http://img126.imageshack.us/img126/6339/fotodw1.jpg) i had to take photo when i make a screen shoot that artifact is not visible. I found when i shift between desktops eg. (Ctrl + Alt + F6) some times its disappears but after some time its coming back.
How to remove that artifact permanently ? forget to mention that i have Radeon 9600 and using  official drivers (8.42.3) currently latest. 

Thx,

I am having this exact same problem, except I am using standard Gnome in Dapper so i would suggest it is NOT a KDE issue perse.

I recently installed an X800GTO in my AGP machine so i thought i would upgrade the driver to 8.42.3 and I am having this problem.

Also i noticed if i open up the Catalyst Control Center then close it, the artifacts disappear.  (until they show up the next time)

if anyone knows how to solve this i would lke to know,

---

### Post by TeaSwigger on 2007-11-20
Would it be possible for you to use the previous driver? Was it working without issue? If so, I suppose I'd go back to it and wait for the next update instead.

Just a thought, have you ran 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

to reconfigure x, and checked the /etc/X11/xorg.conf file to see if the desired driver is actually being used?

---

### Post by lexxonnet on 2007-11-21
Its a known bug in the official 8.42.3 drivers I believe. I had it with both kwin and compiz, and started using the DRI drivers instead. They're a lot more stable, and they work amazingly well with compiz on the 9600 :)

---

