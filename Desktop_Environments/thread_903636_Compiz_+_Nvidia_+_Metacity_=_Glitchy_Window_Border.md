---
title: "Compiz + Nvidia + Metacity = Glitchy Window Border"
date: 2008-08-28
forum: Desktop Environments
---

### Post by kpkeerthi on 2008-08-28
Running Compiz + Nvidia. The window border sometimes goes wacky as seen in the screenshot, but not always. Happens with any GTK theme I have tried.  
[[IMG]http://img119.imageshack.us/img119/2180/screenshotiv2.th.png[/IMG]](http://img119.imageshack.us/my.php?image=screenshotiv2.png)

Does anyone have any idea what's causing this?

---

### Post by kpkeerthi on 2008-08-29
Anyone?

---

### Post by TheSeanKelly on 2008-09-11
I'm having the same problem - would greatly appreciate help!!

---

### Post by CJ56 on 2008-09-11
Happens to me too, only I've got Emerald rather than GTK as Window Decorator...

And I have no idea why

Annoying, isn't it?

:(

---

### Post by dthiessen on 2008-09-24
Same issue here. Does anyone know if a bug has been filed. If not I will try to get one in.

---

### Post by mannheim on 2008-09-24
I think this is something that happens with certain graphics cards and only certain versions of the proprietary nvidia driver. For example, I have a machine with 7600 card. I get the problem described in this thread if I use the nvidia driver 169.xxx.xxx or anything more recent. However, I have no problems with the older version of the driver, version 100.14.19.

I have read somewhere (can't remember where) that this is a problem with some nvidia cards of the 6000 and 7000 series.

---

### Post by teseglet on 2008-09-24
I have a GeForce 6200 and have the problem, particularly with OO Word Processor.

---

### Post by itsjustarumour on 2008-09-26
Same problem here, Compiz with Metacity, NVidia 6800LE card on Hardy 8.04.

---

### Post by Therion on 2008-09-26
Had this problem...  I was ripping my hair out because it was driving me insane.  

I *totally* removed Emerald (I wasn't using it anyway) and the problem was solved. 

Permanently.

---

### Post by kpkeerthi on 2008-09-28
I never had emerald installed. I always use GTK Window Decorator. I have the problem, still.

---

### Post by itsjustarumour on 2008-10-04
> **kpkeerthi said:**
> I never had emerald installed. I always use GTK Window Decorator. I have the problem, still.

Same here - I also get the problem even when Emerald isn't installed...

---

### Post by teseglet on 2008-10-05
Unfortunately experiencing same issue, even to a worse degree with Intrepid Beta.

---

### Post by evilnone on 2008-10-05
i have the same issue after upgrading to the intrepid beta... had no issues before hand...

---

### Post by inigomontoya on 2008-10-05
Which driver version are you using?  I am having no problems with an Nvidia 7000m and driver version 177.78.  What do you have in your xorg.conf?

---

### Post by Therion on 2008-10-16
Emerald comes with Compiz.  If you installed Compiz Fusion, you installed Emerald.

[More explanation...](http://wiki.compiz-fusion.org/Decorators/Emerald)

---

### Post by kpkeerthi on 2008-10-17
I have absolutely no idea what happened. The problem seems to have disappeared now and going on great for the past several weeks. Hope it stays fixed. I'll mark this thread as solved.

---

### Post by shadanan on 2008-11-12
> **kpkeerthi said:**
> I have absolutely no idea what happened. The problem seems to have disappeared now and going on great for the past several weeks. Hope it stays fixed. I'll mark this thread as solved.

I am still experiencing this problem on the latest 8.10 release. I have an Nvidia GeForce 7600GS. 

I have googled extensively for a solution to this problem to no avail. If anyone else has solved this problem and knows what the fix is, any help would be greatly appreciated.

Could this thread be reopened until a repeatable solution is found? Thanks a lot.

---

### Post by LunaEqualsLuna on 2008-11-12
i had the same problem on an nvidia 7400 on my laptop.
what i did was more a work around than a fix.

I went into the themes panel, and chose 'customise' and i change the window title bar from the default 'human' to 'glossy'

There is almost no difference in looks but i no longer get the glitchy window border.

---

### Post by shadanan on 2008-11-13
Luna, I tried your solution, but unfortunately, it doesn't work. Any other ideas? If I disable effects, the problem goes away, so I'm fairly sure it has either to do with the Nvidia driver or compiz.

---

### Post by kpkeerthi on 2008-11-14
The problem reappeared for me now with the 177.80 driver. I'm gonna try with the new [177.82]("http://www.nvidia.com/object/unix.html") over this week-end and post back.

---

### Post by shadanan on 2008-11-14
Actually, I found that if I switch to certain different themes, like darklooks, dust or some of the older looking themes, the problem doesn't exist. It's not solution, but for the moment it will do. Nevertheless, I would still like to know how the new driver works out for you. Good luck.

---

### Post by chrestomanci on 2008-11-14
I have seen a similar problem to this on my laptop. I reported a bug about it:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/272566](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/272566)

My laptop uses an ATI X1600 Graphics, and is using the open source drivers. I found that I only saw the problem when the laptop had been suspended and then resumed.

Are you using a laptop? Have you suspended it?

---

### Post by kpkeerthi on 2008-11-15
Good news. The issue has been resolved in the [180.06 beta driver]("http://www.nvnews.net/vbulletin/showthread.php?t=123072").
> 
From changelog...

Fixed a regression that could result in window decoration corruption when running Compiz using Geforce 6 and 7 series GPUs.

I tested the driver and does seem to fix the window border problem (Yay!) but I got other annoyance - color banding on my desktop, as if the gradients fail to blend properly. So I reverted back to current stable 177.80.

---

### Post by kpkeerthi on 2008-11-15
> **kpkeerthi said:**
> The problem reappeared for me now with the 177.80 driver. I'm gonna try with the new [177.82]("http://www.nvidia.com/object/unix.html") over this week-end and post back.

No luck with 177.82

---

### Post by tayroni on 2008-12-16
I'm using the default 177 nvidia package on intrepid and the issue persists. Even worse on ooo.

---

