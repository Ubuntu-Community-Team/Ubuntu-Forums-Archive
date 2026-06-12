---
title: "multiple xbox 360 wireless controllers with one hub?"
date: 2008-07-05
forum: Gaming &amp; Leisure
---

### Post by mttnry on 2008-07-05
Hey,

I recently went out and bought myself one of those neat, fancy Xbox 360 wireless receivers and <3 it.  I followed this guide:

[https://help.ubuntu.com/community/Xbox360Controller](https://help.ubuntu.com/community/Xbox360Controller)

works great with ubuntu, I have been using joystick calibration to calibrate a single controller. 

Now I have multiple wireless controllers, and I understand with M$XP it works up to 4 controllers at a time.  I was wondering if anyone has any experience getting 2 xbox 360 wireless controllers to work at the same time in ubuntu, and if so how?  I searched the forums and "googled it up" (where I find the answer to most of my ubuntu questions) and **I** havent found anything on this topic.  Again to clarify it works great running one xbox 360 wireless controller through the xbox 360 wireless gaming receiver.  I am wondering how (if possible) to run 2 xbox wireless controllers at once (for two player games :) )

Also seeing as this is my first post I would like to thank the community with all the help in the past.  Whenever I have tried to get something done/running in ubuntu I have always found the answers thanks to these great forums and very helpful people.

--
matt neary

---

### Post by dfreer on 2008-07-05
Hmmm. Unfortunately I only have one Xbox360-style controller, and I haven't even tried getting it working in ubuntu as of yet, so I dunno if I'd be able to help.

But I have run multiple USB gamepads in ubuntu at the same time. And the only thing I can think of is when you set up your second 360 controller, make sure it gets a different /dev/input/ name than the first one.

For example, when I plug in my first USB controller, it gets the name /dev/input/js0 if I remember correctly. The second one will get /dev/input/js1, and so on.

EDIT: I wouldn't recommend installing jscalibrator unless you know for sure you absolutely need it. A lot of people have been experiencing issues with gamepads that would normally work just fine without jscalibrator. But if it already works for you then it works :D

---

