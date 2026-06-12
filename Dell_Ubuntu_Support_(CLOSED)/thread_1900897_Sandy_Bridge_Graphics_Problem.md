---
title: "Sandy Bridge Graphics Problem?"
date: 2011-12-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Karl S. on 2011-12-27
Apologies if this problem has been dealt with elsewhere; I haven't been able to find a solution.

I get horizontal purple bars across the screen sometimes, and more often than not, the system crashes soon afterwards. This happens about 2 or 3 times a day. Totally annoying, and I'd love to know about a fix.


Ubuntu 11.10. Here's the graphics info for my Dell Vostro v131:

VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

Image below is what it looks like (apologies if image too big)

[IMG]http://farm8.staticflickr.com/7023/6581714293_f27b707494_z.jpg[/IMG]

---

### Post by mikewhatever on 2011-12-27
Try Unity2d from the login screen. I suspect these lines may have something to do with the combination of Compiz and the graphics driver. Hope Intel gets it right in a year or two. :~)

---

### Post by collisionystm on 2011-12-27
> **Karl S. said:**
> Apologies if this problem has been dealt with elsewhere; I haven't been able to find a solution.

I get horizontal purple bars across the screen sometimes, and more often than not, the system crashes soon afterwards. This happens about 2 or 3 times a day. Totally annoying, and I'd love to know about a fix.


Ubuntu 11.10. Here's the graphics info for my Dell Vostro v131:

VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

Image below is what it looks like (apologies if image too big)

[IMG]http://farm8.staticflickr.com/7023/6581714293_f27b707494_z.jpg[/IMG]


install compiz settings manager

sudo apt-get install compizconfig-settings-manager

open the compiz config program

click on openGL

uncheck, sync to vblank

set texture filter to fast

log out and back on

---

### Post by Karl S. on 2011-12-27
> click on openGL

uncheck, sync to vblank

Thanks much for the solution, collisionystm (not ready to give up in Unity just yet mikewhatever] 

Just to confirm: Under OpenGL, you want me to disable vblank if it's currently enabled (and then turn the texture filter to 'fast')?

---

### Post by collisionystm on 2011-12-27
> **Karl S. said:**
> Thanks much for the solution, collisionystm (not ready to give up in Unity just yet mikewhatever] 

Just to confirm: Under OpenGL, you want me to disable vblank if it's currently enabled (and then turn the texture filter to 'fast')?

yes then log out and back in

---

### Post by Karl S. on 2011-12-27
Okay, great. Did it. Will give it a day or so to see if the problem reappears. If it doesn't, I'll mark this thread as solved. Thanks much for the help.

---

### Post by collisionystm on 2011-12-27
> **Karl S. said:**
> Okay, great. Did it. Will give it a day or so to see if the problem reappears. If it doesn't, I'll mark this thread as solved. Thanks much for the help.

you should notice things moving a bit snappier too

---

### Post by Karl S. on 2011-12-28
snappier: YES. they are. thanks a bunch. Haven't had the problem since I followed your instructions. marking this as solved.

---

### Post by collisionystm on 2011-12-28
> **Karl S. said:**
> snappier: YES. they are. thanks a bunch. Haven't had the problem since I followed your instructions. marking this as solved.

Good to hear! :D

---

