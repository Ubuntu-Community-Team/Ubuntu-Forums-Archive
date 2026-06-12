---
title: "Latitude C840 = Painfully sluggish &amp; messed up"
date: 2007-07-12
forum: Dell  Ubuntu Support
---

### Post by Aksumka on 2007-07-12
I have Fiesty running on this laptop, and for some reason it is just so slow. Spec wise, the laptop is just fine:
1.6 Ghz P4
512 MB RAM (upgraded)

I don't know why it is running so slow. Everything I do takes longer than it should. I really can't do much with it like this. Even browsing the net is a painful experience.  Icons take long to load, running anything takes forever to start up.

I think it may be the video drivers as the start up screen laggs to load. I see white, and then it moving down in bars. I also have problems with closing the lid. When I do, I have it set to do nothing when on AC power. But, when I do close it, the screen blacks and stays that way even after I've opened it. The only way to get back the display it to press the function key with the display switch button. But that just allows me to see something again, the problem is that something is a messed up version of whatever I have on the screen. The top and bottom bars meet at the middle of the screen, and all other windows are cut off at the bottom and continue at the top (of the screen). Ubuntu does not know of this problem. I can take a screenshot, but that screen shot is of the normal desktop. The mouse will continue to work as normal though, and I can click something if it is where it is in the real desktop.

I really don't know what is going on, I'm not exactly "new" with Ubuntu, but I'm no pro.

---

### Post by mozetti on 2007-07-12
Have you installed the nvidia driver? I used to use one of those for work, and had loaded Breezy on it and it worked great. IIRC, the C840 had an Nvidia Geforce 420Go video card. Use tseliot's HOWTOs for the Nvidia drivers and it might sort out your problems.

---

### Post by Aksumka on 2007-07-12
Cool, well I did that, it ran (i think), I restarted and now the screen won't go on.

It's not black, it just off...


I now have the laptop hooked up to a spare monitor, so now I can at least see what is going on. The drivers appear to have done nothing. It is still slow, and colors remain in like 16 bit.The only way I can get the screen to work again is to disable the restricted driver.

---

### Post by Aksumka on 2007-07-13
Anyone? I need this problem fixed in like 2 days...

Sorry if this post seems "needless."

---

### Post by fnandocc on 2007-07-21
Same problem. follow this thread.

[http://ubuntuforums.org/showthread.php?p=3057699#post3057699](http://ubuntuforums.org/showthread.php?p=3057699#post3057699)

short version: Edit your /etc/X11/xorg.conf

with this:

[http://pastey.net/71135](http://pastey.net/71135)

make sure that the nvidia-glx driver is installed.

---

