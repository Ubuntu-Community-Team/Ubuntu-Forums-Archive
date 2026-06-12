---
title: "Alienware M15x and Nvidia Gtx 260m Random Crash"
date: 2011-05-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by netman_zion on 2011-05-18
Well i have a fresh Ubuntu Natty instalation and just randome (5 mins to 4hs) my Xserver crash and sent me to Gdm Login screen.

I  already have installed latest Nvidia drivers 270.41.06, any one is having the same problem ?

Regards

---

### Post by appan on 2011-05-28
I am having the same issue as user netman. Not sure what to do any help is appreciated . thanks.
I have nvidia GTX 260M on the alienware 15x and random restart in Unity and classic (11.04 64 bit). It can be every 5 -10 minutes or sometimes after 1 hr.. No reboots or crashes in WIndows 7 64 bit

---

### Post by wh20250 on 2011-05-29
I have the same issue. I have noticed it happens most often while running on battery and using the browser. I also had this problem in 10.10 and hopped a fresh install of 11.04 would fix it. Unfortunately no dice. I really hope some one can shed some light on this issue soon.

---

### Post by netman_zion on 2011-06-06
Well i already updated to the latest Nvidia Driver 270.41.19 and still have the problem, this happen to on Ubuntu 10.10 and now with a fresh install of Ubuntu 11.04

I test the Stable Nvidia driver 173.14.30 but this sucks all the computer turn on to slow

Any one have any idea ?

Regards.

---

### Post by netman_zion on 2011-06-13
Bump, i still have with the same problem

Any help can be useful

Regards

---

### Post by reza_e13 on 2011-06-24
hi,
I have the same alienware m15x with gtx 260. the only trick that I have found in other forums is to run glxgears and then enable and disable the stealth mode button.
after that I won't get any crash, but i should do this trick on every restarting of the system ;)

---

### Post by Humberto_H on 2011-08-09
I have the same Computer and Video Card with the same problem, I have a power point file that when run on battery produces the crash. 

has anybody checked the xorg and gdm log files?

Humberto

Here is a link to the file that will be working for 30 days

[http://www.filedropper.com/sobreperros](http://www.filedropper.com/sobreperros)

---

### Post by wh20250 on 2011-10-04
From what I have discovered on my m15x is that it is a stealth mode issue. Try booting into windows and see if stealth mode is on. Once I disabled it in windows... poof no more crashing, unless I inadvertently press the button.

---

### Post by mdog on 2011-12-28
Long running thread, I know, but this problem has been the bane of my existence since I got the Alienware m15x with a core i5 M-540 and Nvidia GTX-260M.

The stealth mode button is definitely the issue and if you have your nvidia driver set up to be in "adaptive mode" it will crash a lot.

Crashes are more frequent with certain driver/kernel revisions for me, but recently I tried to add this kernel parameter to "/etc/default/grub" (run "update-grub2" afterwards):

intel_iommu=igfx_off

And since I did this I've had no crashes, even with adaptive powermizer settings and running the laptop for hours every day for a week 

The setting turns off the graphics part of my core i5 as far as I can tell and therefore won't try to switch between the intel and nvidia GPUs.

I wanted to supply this possible solution since I haven't been able to find it mentioned with this laptop. Of course it will crash about 5 minutes after I post this :D

---

