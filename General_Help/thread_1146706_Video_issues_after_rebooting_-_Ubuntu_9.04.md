---
title: "Video issues after rebooting - Ubuntu 9.04"
date: 2009-05-02
forum: General Help
---

### Post by Mirge on 2009-05-02
I wanted to make use of compiz, so I used the proprietary hardware drivers for my ATi card... it said I need to reboot for the changes to take effect.. so I rebooted. Much to my dismay, when I rebooted... and it tried to fire up X, I am (still) stuck at a black screen... but not solid black.. it's 95% black with some color kinda wiped across it I guess... almost like your refresh rate is too high?

I tried dpkg-reconfigure xserver-xorg -- but same thing is happening. Please advise :(.

Here's a picture of someone elses that looks almost identical to mine:

[img]http://i386.photobucket.com/albums/oo309/divxclub/04292009036.jpg[/img]

---

### Post by Mirge on 2009-05-02
After some searching:
[http://ubuntuforums.org/showthread.php?t=1135107](http://ubuntuforums.org/showthread.php?t=1135107)

> **zancoste said:**
> I was able to fix the problem :)

Reboot your computer into recovery mode, choose root prompt perform the followings:
```
sudo apt-get remove xorg-driver-fglrx
```Then try to start normally. Now if it works but the resolution is messed up, you can always run 
```
sudo dpkg-reconfigure xserver-xorg --frontend=gnome
```It worked for me :)
I hope it does for you too.

This solved the problem for me! Thought I would make the effort to come back and say specifically what solved the issue for me in case others ran into this as well. Can't hurt!

Of course, I can't use compiz without a proprietary driver heh... so I guess no compiz for me until I get a different video card =(.

---

### Post by Mirge on 2009-05-02
Ok, I take back my previous statement! I just went to ATi's site and downloaded the latest Linux x86_64 driver for my card... and it worked PERFECTLY... hellloooo compiz :).

FYI, driver was released 4/17/2009...

---

### Post by Mirge on 2009-05-07
Well there I go tinkering again... for dual monitor support. Ended up at the same scenario as my original post (see picture earlier in thread). Seeing nearly exact same thing.

The fix I used before isn't working this time though...

I actually get this error:

unable to initialize frontend: Gnome
DISPLAY PROBLEM?


Please help ASAP if you can, this is my work PC and I need it in a few hours heh...

---

### Post by kooky_LT on 2009-05-07
Did you install any software to make your dualmonitor work?

---

