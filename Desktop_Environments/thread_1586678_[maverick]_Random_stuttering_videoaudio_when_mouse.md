---
title: "[maverick] Random stuttering video/audio when mouse NOT moving"
date: 2010-10-02
forum: Desktop Environments
---

### Post by H3g3m0n on 2010-10-02
Since updating to 10.10, randomly sometimes the CPU usage will just up (although it's generally only 1 of the cores), it seems that it might be the Xorg process using it.

Audio and Video will start to stutter and the screen will stop updating so things like the terminal will appear frozen unless the mouse is moved.

When moving the mouse the screen keeps updating and the cpu usage lowers (although video still skips).

After a few minutes the problem just seems to go away until it happens again later.

Using the nvidia drivers.

---

### Post by iMerlin on 2010-10-10
Experiencing this as well. Appears to be everything in X11 though. Typing sometimes slow as well.

CPU load:  0.52, 0.41, 0.45

The only processing consuming unusually much CPU is xorg

Just upgraded from Lucid, disappointed :(

---

### Post by thndrkat on 2010-10-11
Experiencing this issue also on a toshiba nb305 netbook.  Music/video sticks if the mouse is not moved periodically. Also, I have noticed strange behavior during boot that 10.10 will not load if I don't move the mouse.

---

### Post by Morrog on 2010-10-12
i'm also experiencing this rather annoying problem, on a dell inspiron 1750. i didn't have it in 9.10 or 10.04

this seems to be a working solution for me, so far:
> 
gksudo gedit /etc/pulse/default.pa
and then add tsched=0 to the line with 'load-module module-udev-detect'

so it becomes:
load-module module-udev-detect tsched=0

---

### Post by GartenEden on 2010-10-13
Same problem here. For me Morrog does NOT work.

---

### Post by zuerston on 2010-10-13
Same here at times, also see my post about Firefox video, it could be related.

---

### Post by tomsib2001 on 2010-10-14
Same problem here. This is really annoying. The proposed solution does not work.

---

### Post by Eric89GXL on 2010-10-15
Same problem. Is there a bug report somewhere we could subscribe to?

EDIT: I couldn't find one, so I submitted one:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/661327](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/661327)

---

### Post by schneil on 2010-10-16
Hi all

Got exactly the same problem on my dell latitude D505.  Stuttering audio, seems to follow a regular cycle, about once every 5 seconds.
Didn't have this problem in 10.04 or 9.10.  

Very annoying as I use the laptop for spotify, last fm and the rest.

---

### Post by Eric89GXL on 2010-10-16
If we want this fixed in a timely fashion, it would help if people could subscribe to the bug and post that they are experiencing the issue, too. We can also try to narrow down what is common to all of our systems, if anything. In the report I submitted, all of my hardware is listed... if people could subscribe and post their configurations, it could help the devs track down the issue. 

Speaking of which, is anyone experiencing this not using an NVIDIA graphics card? I am, and I had this problem with both the proprietary drivers and nouveau.

---

### Post by RJARRRPCGP on 2010-10-16
> **H3g3m0n said:**
> 

the screen will stop updating so things like the terminal will appear frozen unless the mouse is moved.

When moving the mouse the screen keeps updating 

God, that sounds like the stupid QEMU virtual machine bug I remembered seeing, when using XP on QEMU. 

One bizarre bug!

---

### Post by glaeken on 2010-10-22
Same here, Acer Extensa 5630EZ
tshed=0 somewhat elminated the problem, BUT some applications still need mouse movement to refresh properly.
What is more interesting, VERTICAL movement.
:D

---

### Post by dimeotane on 2010-11-04
Same problem here on Toshiba NB205

Could it be related to this post?
[http://www.uluga.ubuntuforums.org/showthread.php?p=9948670](http://www.uluga.ubuntuforums.org/showthread.php?p=9948670)
His issue he says is from IPv6 being active by default.

---

### Post by Eric89GXL on 2010-11-11
The issue was resolved for me by upgrading to the 2.6.36 kernel, which you can get from the mainline ppa.

---

### Post by dimeotane on 2010-11-16
Thanks Eric, giving this a shot now.  This problem has been so annoying without a fix from Ubuntu updates. 10.10 has been a frustrating experience so far, with too many problems.  

I've gone to : 

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-rc2-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-rc2-maverick/)

and I'm downloading the linux-headers and linux-image for i386 now. Hope this solves it for me too.  I'll report back later.

---

