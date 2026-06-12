---
title: "dual screens for radeon x1950xt"
date: 2008-01-23
forum: Desktop Environments
---

### Post by feras on 2008-01-23
So, I really don't know much about linux and just installed ubunutu to force myself to learn more.

I do alot of web development primarily on my windows computer, but my servers are linux based so I know some basics.

Anyways, I have a x1950xt and want to be able to run dual screens, mostly so I can drag things around and what not.

I tried google, but didn't see any good guides. Does anyone know how this can be done?
Any help is greatly appreciated!

---

### Post by shonisan on 2008-01-23
Search the forums:

This is to make sure you have the drivers installed:
[http://ubuntuforums.org/showthread.php?t=515573](http://ubuntuforums.org/showthread.php?t=515573)

This is for External monitors:
[http://ubuntuforums.org/showthread.php?t=301941&highlight=ati+external+monitor+x1950](http://ubuntuforums.org/showthread.php?t=301941&highlight=ati+external+monitor+x1950)

---

### Post by Prospero2006 on 2008-01-23
First, congratulations. You have made a good choice. The Ubuntu learning curve is totally worth it. (You might also want to try Linux Mint, which is based on Ubuntu, but comes with some out of the box configuration that makes a few things easier.)

Ok, dual screens:

xorg.conf:
 
The configuration file for monitor support is located in:

/etc/X11/xorg.conf

By manually editing that file, you can control how many monitors you are working with. 
I have one computer at my desk that has 3 heads set up. The number of monitors you can configure is only limited by the number of card slots on your motherboard. 

Learning to work through xorg.conf is a tricky endeavor, but it all fits together logically.
It's commented well, and there are a lot of threads relating to how this file works to control monitor setup.


Drivers:

ATI drivers are pure hell on Linux. That's all there is to it. Anyone who disagrees with me on this point is itching for a fight. You have to download the binary, run a command that is suffixed by  --buildpkg Ubuntu/gusty, install the debs manually, blacklist modules, and enable new ones. (Fortunately, the step-by-step instructions provided above are easy to follow.) If the first driver you try doesn't work, try an earlier version. The newest ATI driver release doesn't want to play nice with my X300 series card, so I use an older driver, which has ok performance. 

So, here's what you should do:
    -First, make sure ATI drivers are set up and running correctly. Verify OpenGL.
    -Then, get in and start hacking xorg.conf.

Good Luck!

---

### Post by feras on 2008-01-23
Thanks for the links shonisan.

hey Prospero,
thanks for the write up. I just need to mess around a bit and get familiar.
I will try the tutorials tonight when I get home. Just curious, how can I very OpenGL?

Also, on another side note, when browsing through the menus I found the displays menu. I have dual Samsung 216BW's. I couldn't find them listed there, and tried a few others, and when I tested I couldn't get them to show up. I was just trying to resolve my resolution issues. Any ideas?

Thanks again!

---

