---
title: "adding undetected resolution in gdm"
date: 2009-03-09
forum: Desktop Environments
---

### Post by Darth_Maga on 2009-03-09
Hi everybody

could someone give me a hand in this pls?? (ubuntu 8.04)

I have a laptop with intel 810 integrated graphics. so far so good; but for some reason mode 1280x1024 is'nt detected, which is the resolution preferred by my external screen. So I run "xrandr -- addmode VGA 1200x1024" and afterwards "xrandr --output VGA --mode 1280x1024" to get the external monitor working, but it is a bit of a drag. I would like to add the 1280x1024 resolution early in the boot process so the screen starts up by itself in correct mode, I suppose by including the 1st line in gdm, but WHERE?? WHICH SECTION??

tks vm for help guys

DM

---

