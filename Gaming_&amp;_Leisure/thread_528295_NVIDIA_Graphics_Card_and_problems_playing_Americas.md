---
title: "NVIDIA Graphics Card and problems playing Americas Army"
date: 2007-08-17
forum: Gaming &amp; Leisure
---

### Post by Ted_Smith on 2007-08-17
Hi

I wasnt sure whether to put this in Hardware or gaming, cause it's kinda both! 

I own two machines of similar but differing specs, and the long story short is I took my NVIDIA Geforce FX5600 256Mb video card out of one machine and put it in another and re-installed Ubuntu on both. 

Previously, running on Dapper Drake and an AMD 2600XP CPU, my NVIDIA card, and more to the point, Americas Army 2.5 ran fine. I had top level graphics with no problems. 

Since swapping to the new machine (with dual Intel Xeon 1.7Ghz SMP processors) and running AA on Feisty Fawn, I have a weird problem. Basically during game play, every few minutes the screen goes blank for about 3 seconds, then it comes back. Annoying, but not the end of the world. However, after a while the game kind of crashes, or seems to, for about 20 seconds, then it comes back but all the screen has 'flecks' all over it. It's hard to describe, but it's like an 8 bit version of the game combined and overlayed with a full version. Screenshot below : 

[IMG]http://www.k9blog.co.uk/screenshot1.jpg[/IMG]

When I run glxgears I get about 2284 fps. It too has the same weird flickering but only when the game starts to get it. Prior to that it looks fine. 

[IMG]http://www.k9blog.co.uk/glxgears.png[/IMG]

My kernel is 2.6.20-16-generic and I am using the Restricted NVIDIA Drivers using the 'Restricted Drivers' facility. I have also tried installing the drivers manually using the Envy script. 

Can anyone help me? What can I do to trouble shoot this?

---

### Post by Ted_Smith on 2007-08-18
I have done further reserch, and although I have not fixed the problem, I discovered the following. 

Apparently, there is an issue with the 2.6 SMP kernel with dual processors and some graphics cards. Subsequently, I read that applying the following settings to the kernel boot parameters at startup may help : 

pci=nommconf idle=poll 

I have tried both, and my system failed to boot. So I tried them one at a time (which allowed the system to boot) and played Americas Army. The problem persists.

Any other ideas? 

Thanks

Ted

---

### Post by Ted_Smith on 2007-08-20
From what I have read since, this almost certainly appears to be related to the fact I have two Intel processors and is to do with a conflict of some sort between the 2.6 kernel and the Nvidia restricted drivers. 

I have just read that there's another kernel option to try, maxcpus=1, which will turn a dual system into a single CPU system. That may solve the problems I am having with the graphics, but it will make my dual system into a solo system which defeats the point. I am yet to try it (will let you know if it works) but if this is the case, it's a horrible siutation for Linux users to be in.

---

### Post by tseliot on 2007-08-20
Did you try asking here?
[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)

---

### Post by Ted_Smith on 2007-09-09
Thanks, and no - I hadn't tried there. I posted a thread straight away but to date it still remains unanswered. 

It seems I have struck upon a rather rare and unusual problem for which only the mightyist of Linux users will be able to solve!

---

