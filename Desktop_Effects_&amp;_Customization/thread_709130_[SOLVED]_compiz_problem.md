---
title: "[SOLVED] compiz problem"
date: 2008-02-27
forum: Desktop Effects &amp; Customization
---

### Post by darkside299 on 2008-02-27
I have ubuntu 7.10 installed on my PC. I have got 512 MB RAM with intel 865GBF Motherboard which has got Intel® 865G Chipset with Intel® Extreme Graphics 2.

I have compiz enabled on my Pc. Now,it workd very smoothly in general. But some times (rarely) the window frames and title bar suddenly disappear. It happened especially when I was doing fast ALT+Tab. Why is the problem occuring? How to solve it?

Also I am not able to initialize Desktop cube. My PC almost hangs when I try it. Dos it require a special graphics card?

---

### Post by Sam Lars on 2008-02-27
From a command line
```
compiz --replace
```
should get your frames back.
When it happens again, check that terminal to see what it says, if anything, about it.
About the cube... yes, I would thing that it's a fairly intensive effect.  Intel onboard graphics aren't the best, you could try a new video card if it's worth it to you.  I got one for $60 that's more that sufficient.

---

### Post by darkside299 on 2008-02-28
OK, Thanx, I will do it when it happens and reply on thi thread about the result.

---

### Post by darkside299 on 2008-03-11
It worked. Thank you.

---

