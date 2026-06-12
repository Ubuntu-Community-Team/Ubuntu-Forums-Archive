---
title: "any chance unity will run better on xubuntu?"
date: 2012-08-12
forum: Desktop Environments
---

### Post by LLCoolJeff on 2012-08-12
few questions regarding unity for a noob who doesn't understand linux too well.

Unity ran terrible for me on Ubuntu 12.04, although I did like it otherwise. I opted for a clean install of xubuntu to have everything fresh, and XFCE runs awesomely. I was thinking of installing unity for fun to mess around with if I felt like it but I have a few concerns, since I am not too familiar with the inner workings of linux and how things interact.

0. Will it work?
1. Any chance unity will run any better off my xubuntu install?
2. Any chance after installing unity, my XFCE part of the system will slow down?
3. Will the unity environment install a bunch of duplicate system apps? (I had this happen on ubuntu 12 and some other DE's on a previous install)

EDIT: P.S. my laptop is not hot off the press, but its not old either (AMD vision dual core 2.1 ghz, 512 cache, ATI radeon 3200, 4GB ram) so why would unity run slow on this machine? CPU's were always at 100%, even idling, being taken up by Xorg and something else I don't remember.

EDIT 2: I was running Ubuntu 64 bit, but I had also tried 32 bit and they were both the same slowness...

---

### Post by alan21276 on 2012-08-12
If you install unity back onto xubuntu you are effectively turning your installation back into stock ubuntu. And hence will lose the speed gain from light weight xfce.

The letter pre-fix to ubuntu i.e lubuntu, xubuntu, kubuntu simply refers to the front end and you cant run more than one at the same time.

I'm sure someone else on here could explain this more articulately, but that is my understanding of it.  


Have you tried unity 2d ?

---

### Post by LLCoolJeff on 2012-08-12
I did try unity 2d when I had ubuntu installed and it was just as slow. I did a lot of playing around trying to figure out why it was so slow with no success so I finally gave up, it sucks because I really wanted to use Unity....

I know that the prefixes mean the different DE's of ubuntu, but you said that installing unity would slow down any speed gain from XFCE, so would that mean after I install Unity, even when i am logged into XFCE, it would now be slower just by having Unity on the system?

---

### Post by vasa1 on 2012-08-12
> **LLCoolJeff said:**
> ... **CPU's were always at 100%**, even idling, being taken up by Xorg and **something else I don't remember**.
...
1. Something is terribly wrong. 
2. BTW, you better remember. Helps people help you :)

Also, whether any part of your problems is dues to the ATI Radeon stuff is an issue.

---

### Post by LLCoolJeff on 2012-08-12
> **vasa1 said:**
> 1. Something is terribly wrong. 
2. BTW, you better remember. Helps people help you :)

Also, whether any part of your problems is dues to the ATI Radeon stuff is an issue.

I was trying to remember, but I couldn't and the install is now gone so there is no way for me to tell. 

My main worry is whether installing unity on my system now will have any damaging effects... Even when I login to XFCE and not Unity....Any final word on that?

---

### Post by vasa1 on 2012-08-12
> **LLCoolJeff said:**
> I was trying to remember, but I couldn't and the install is now gone so there is no way for me to tell. 

My main worry is whether installing unity on my system now will have any damaging effects... Even when I login to XFCE and not Unity....Any final word on that?
No final word. Stay with vanilla Xubuntu for at least a few days. See that everything is fine, none of this CPU usage at 100%, etc for all the stuff you like doing.
Keep a close eye on the CPU usage.
If you keep changing, you and those trying to help are going to get confused.

---

### Post by LLCoolJeff on 2012-08-12
> **vasa1 said:**
> No final word. Stay with vanilla Xubuntu for at least a few days. See that everything is fine, none of this CPU usage at 100%, etc for all the stuff you like doing.
Keep a close eye on the CPU usage.
If you keep changing, you and those trying to help are going to get confused.

ok, I will stick to this for a while although I am pretty sure the CPU issue is nonexistant in Xub'

---

### Post by 3Miro on 2012-08-12
> **LLCoolJeff said:**
> 
0. Will it work?

Xubuntu uses xfce and Unity uses Gnome 3 + Compiz. You can have multiple DE installed, so technically YES it will work.

> 
1. Any chance unity will run any better off my xubuntu install?

No. Unity on Xubuntu is the exact same Unity as in Ubuntu.

> 
2. Any chance after installing unity, my XFCE part of the system will slow down?

No. Unless you start running Gnome specific apps, in which case it may slow down. If you are using xfce just as you are using it now, then it will not slow down.

> 
3. Will the unity environment install a bunch of duplicate system apps? (I had this happen on ubuntu 12 and some other DE's on a previous install)

Some apps will be duplicated. For example, you will have both Thunar and Nautilus for file managers. Unlike KDE, xfce comes with fewer default apps and hence the duplicated should be few.

> 
EDIT: P.S. my laptop is not hot off the press, but its not old either (AMD vision dual core 2.1 ghz, 512 cache, **ATI radeon 3200**, 4GB ram) so why would unity run slow on this machine? CPU's were always at 100%, even idling, being taken up by Xorg and something else I don't remember.

Some time ago AMD stopped supporting this model of video cards for Linux. Hence, any graphical environment that requires visual effects (like Unity), will not run well. My advice is to stay with xfce or lxde (i.e. no visual effects).

> 
EDIT 2: I was running Ubuntu 64 bit, but I had also tried 32 bit and they were both the same slowness...
The video driver issue exists in both 64 and 32 bit versions.

---

### Post by LLCoolJeff on 2012-08-12
> **3Miro said:**
> Xubuntu uses xfce and Unity uses Gnome 3 + Compiz. You can have multiple DE installed, so technically YES it will work.


No. Unity on Xubuntu is the exact same Unity as in Ubuntu.


No. Unless you start running Gnome specific apps, in which case it may slow down. If you are using xfce just as you are using it now, then it will not slow down.


Some apps will be duplicated. For example, you will have both Thunar and Nautilus for file managers. Unlike KDE, xfce comes with fewer default apps and hence the duplicated should be few.


Some time ago AMD stopped supporting this model of video cards for Linux. Hence, any graphical environment that requires visual effects (like Unity), will not run well. My advice is to stay with xfce or lxde (i.e. no visual effects).


The video driver issue exists in both 64 and 32 bit versions.

thanks for taking the time to reply, I think the problem is clear now. I always suspected it was the video card, but wasn't sure

---

