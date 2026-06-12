---
title: "compiz fusion slow down"
date: 2007-08-10
forum: Desktop Effects &amp; Customization
---

### Post by zero-9376 on 2007-08-10
i have an 8600GT and i am running compiz-fusion, it runs quite well with just a couple of problems, my biggest concern at the moment is the huge slowdown that occurs after a few hours, when i first boot the computer i get around 100-150fps with the compiz benchmark, after a few hours it drops to around 50 and decreases the 30 when i rotate the cube, the problem is that the 30fps seems slower than the 20 i used to get on my old system, definately more jerky? anyone have a reason and maybe a fix.
This is not about fusion being slow, i know it can be fast and it is at first but slows down dramatically.

---

### Post by Jouke74 on 2007-08-10
What is your memory use, does it steadily increase when you are using Compiz? That might indicate a memory leak. After a while, when your memory is full, it will start swapping to your swap drive, which makes everything very slow.

---

### Post by zero-9376 on 2007-08-18
it seems to be associated with the number of windows on screen, so i guess I will have to live with it. perhaps running dual monitors is having a imapact also

---

### Post by alvinistic on 2007-08-19
I second that! I actually run compiz fusion with Xgl. The moment I start CF it is really smooth and Xgl only takes around 30 MB of RAM. After hours of use it becomes really sluggish and Xgl takes 100+ MB RAM! I believe the same thing also happens when using Aiglx.

As a side note, I also experience the sluggishness after long use even when using xorg and desktop effects is turned off.

Anybody got an idea why? Thanks.

---

### Post by zero-9376 on 2007-08-27
using the command 

compiz --replace --indirect-rendering 

has made compiz ALOT faster, I think this only applies to nvidia cards, but i cant remember seeing it in the howto i used

---

### Post by kayeaco on 2007-09-06
I meet the same problem.

When I start my computer and login into the system.

Compiz Fusion run fastly and smoothly. However, When I use for 10 or 20 mins later, the system is slow down. Even I just open 1 or 2 window on my desktop, it still slow.

---

