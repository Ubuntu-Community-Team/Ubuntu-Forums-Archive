---
title: "Compiz, Youtube and Mplayer"
date: 2008-03-24
forum: Desktop Effects &amp; Customization
---

### Post by grahambo2005 on 2008-03-24
Hi All

Having an issue with MPlayer Compiz and Youtube

I have compiz working without using XGL

the graphics card is an ATI X1650

The 2 problems im having are: 

1: when I go to you tube and watch a video its fine until i "fullscreen" the video, it pops up for like 1/4 of a second and then disappears

2: Mplayer playback is patchy, it shows me a blue screen every 1 second then continues playng the video for another second and the blue sreen pops up again.

this only happens when I have compiz enabled

any suggestions

---

### Post by lumberjack on 2008-03-26
Well, it's pretty clear that you're having a software issue.  The ATI drivers are good, but are pretty difficult to set up with compiz.  I had a similar issue with my ati card, and it's not really a problem, per se.  your drivers may still be using some form of software rendering (mesa3D) which will drastically slow down performance with 3d.   I used to have triangular artifacts with compiz, until i finally installed xgl.  Xgl makes compiz run like a dream, but it kills any kind of 3d game i try to run.  i ended up making a script to enable 'eye-candy' mode or 'gaming' mode, which in operation only temporarily disables or enables xgl.  since xgl is needed to run in my setup, compiz doesn't start up when xgl is disabled.

Try checking your ati config again and see if you're still using mesa3d.  Otherwise, you may have to try some other things.

---

