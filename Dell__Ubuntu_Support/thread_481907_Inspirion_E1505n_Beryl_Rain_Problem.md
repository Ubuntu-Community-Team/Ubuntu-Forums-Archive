---
title: "Inspirion E1505n Beryl Rain Problem"
date: 2007-06-23
forum: Dell  Ubuntu Support
---

### Post by El Lance-O on 2007-06-23
I just bought one of the new Dell laptops, and I must say, I AM IMPRESSED.

I have never owned a laptop before, and this was definitely a good first choice.

Anyways...here's the problem. Whenever I use any of the water effects with Beryl, this happens:

[[IMG]http://img20.imageshack.us/img20/861/rainproblemgo2.th.png[/IMG]](http://img20.imageshack.us/my.php?image=rainproblemgo2.png)

I'm using the nNVIDIA GeForce Go 7300 video card, any ideas?

---

### Post by El Lance-O on 2007-06-25
Come on people, the water effect is my favorite with beryl, and I'd really like some help fixing it.

---

### Post by El Lance-O on 2007-06-26
Please?

---

### Post by robrmd9 on 2007-06-26
Reread your original post.  It doesn't appear that you have described what happens when you try to use the water plugin.  I don't see a description or attached screen shots.

---

### Post by El Lance-O on 2007-06-28
Actually I did post a screenshot. But here is a better description anyways.

It's actually quite basic, it's just the ripples become really pixelated and spreads to the edge of the screen, then stays there flashing for a bit, disappearing after awhile.

Not much else to say..

---

### Post by robrmd9 on 2007-06-28
Hey Lance-O, looks like my work blocked the image so I couldn't see it (my bad).

Is the water ripple effect in the extra plugins?

---

### Post by defishguy on 2007-06-28
I had a similar problem on mine when trying to use compiz fusion.  I fixed it by installing the intel driver and using that instead of the 810.

> sudo apt-get install xserver-xorg-video-intel

It will automagically remove the 810 driver.  I recommend rebooting before trying anything out.

Good luck!

---

