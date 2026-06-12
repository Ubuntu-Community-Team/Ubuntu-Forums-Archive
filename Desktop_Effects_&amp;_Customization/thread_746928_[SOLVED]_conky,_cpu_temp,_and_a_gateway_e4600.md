---
title: "[SOLVED] conky, cpu temp, and a gateway e4600"
date: 2008-04-06
forum: Desktop Effects &amp; Customization
---

### Post by mandrill on 2008-04-06
Yep, there ya have it. Research through google (I have the pc handbook now) does not indicate any mobo or cpu specs, but here is what i DO know about it. (mostly it likes gutsy with gnome better than any form of windows) It has a 1.8ghz cpu, 400 bus speed, 1 gb of ram (512 x2) and a 240mm back fan that does all the work. Any way, I was playing with conky today (that's interesting) and heard about lm-sensors, so I installed them, no luck,                                      

Then this: jim@monkey:~$ sudo sensors -s
[sudo] password for jim:
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

So having gone that route 3 times today (sensors-detect) I said what the heck and tried it again, while writing this, and instead of just stopping and hanging forever,  it actually worked, It scanned a buncha stuff and installed a buncha stuff! 

If you don't hear back from me, it worked!

---

