---
title: "Inspiron 6400 with ATI x1300 Screen rez"
date: 2007-06-20
forum: Dell  Ubuntu Support
---

### Post by smitty2point0 on 2007-06-20
What's up! I'm having some problems with my screen resolution on my Dell Inspiron 6400. No matter what setting I choose, it never changes!!! It pops the screen and asks if I want to keep the settings or restore previous? I'm pretty sure it's stuck on 1280X800....which isn't bad...but I would like to make it a little higher, or lower if I wanted. What gives?

Also, I can't seem to get a skydome background image to work. If I choose an image, it's never there, and it seems to slow my cube down a tad. I've tried every size image recommended in the forums.

spex...Core 2 duo 1.6, 2 gig RAM, ATI X1300, 80 GB HD, Dual boots to Ubuntu or Vista, 40GB partition for each.

Thanks!

Justin

---

### Post by Paul S on 2007-07-10
To use an ATI X1300 with desktop effects, you have to use the fglrx driver and then load xgl on top of it.  Once you load xgl on, you cannot change the resolution.  Xgl is a "hack" to make it possible to run desktop effects.  But, xgl is not very configurable.

If you want to change the resolution, you have to disable xgl, then it will change.  Once you get it set, then re enable xgl and desktop effects and they should work at the new resolution.

Or, buy an nvidia card and replace your ATI with it.  That works even better.

HTH

---

