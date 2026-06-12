---
title: "Yet another WoW / Cedega / Wine topic"
date: 2006-08-18
forum: Gaming &amp; Leisure
---

### Post by Zay on 2006-08-18
I just cannot get my WoW to run smoothly on either wine or cedega.
I *think* it has something to do with my opengl setup, but I have no idea how to check it. 
Glxgears gives me about 7k fps. It strikes me as low as I look at other posts. (2ghz laptops having same fps)

my system specs:
cpu: AMD athlon 64 4200+
mem: 2gb DDR2
video: Geforce Extreme N6600GT (256MB DDR3)
ubuntu 6.06 (32 bit version)

I have added gxApi line etc on my config.wtf file, added -opengl in cedega (or added it on commandline).

But strangely enough, using d3d is giving me ~20 fps in wow, opengl about 1-5.

My device in xorg.conf is setup on 'nvidia' driver. I'm no longer running XGL, so that can't be bugging too.

I also read some stuff on software and hardware opengl. How can I check which type I am using now, and how can I set it to hardware?

Please tell me if you need more info.

Thanks for your time.

---

### Post by Zay on 2006-08-21
*bump*

I have been playing on d3d some days now, with a playable fps. However, having 15-20 fps is ofcourse crap compared to the 50 fps I had on windows...

Anybody got suggestions that might help me run opengl? thanks.

---

### Post by Zay on 2006-08-22
I hate to answer my own topic, but I have found the problem... kind of by accident.

I have 2 monitors. It was setup with Xinerama. I found out that doesn't support opengl hardware rendering. I am now using twinview (i have an nvidia card) and it is working perfectly now, although the fps is still a bit less then I had in Windows though... :(

Anyway, I hope this may help somebody with the same problems.

---

