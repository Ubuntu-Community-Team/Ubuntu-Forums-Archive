---
title: "are the ati fglrx drivers really that crappy"
date: 2006-12-10
forum: Gaming &amp; Leisure
---

### Post by manatawady on 2006-12-10
Hi there - 
i received a "new" radeon 1650 pro yesterday. After fiddling with installation and things like that i know the fgrlx is running.

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series Generic
OpenGL version string: 2.0.6174 (8.31.5)

glxinfo | grep rendering
direct rendering: Yes


the chipset as it seems is supported.
Somehow i have enormous framedrops within my fav game enemy-territory.
At max i only have 4-7 fps - so unplayable.

What i dont understand is: are the drivers really that crappy?
Is someone able to play with the proprietary drivers in fs?

cheers

PS: as i was posting this before my gnome-session froze - hope i dont double post :(

1280x1024 ubuntu 6.06 lts

---

### Post by fng on 2006-12-10
> **manatawady said:**
> What i dont understand is: are the drivers really that crappy?

ya really!

---

### Post by skwillz on 2006-12-10
I have a Radeon 9600 Pro and ET runs in linux just like it does in Windows. Did you follow a guide to install the fglrx drivers? Maybe something was left out like AGPGart.

---

### Post by Shatrat on 2006-12-10
As someone who has had both nvidia and ati hardware, I'm gonna have to vote for YA RLY!

---

### Post by jetthe on 2006-12-10
> **manatawady said:**
> 
-snip!-
Somehow i have enormous framedrops within my fav game enemy-territory.
At max i only have 4-7 fps - so unplayable.

What i dont understand is: are the drivers really that crappy?
-snip!-


I have to agree with skwillz, ET-based games (i.e. TC:E) runs perfectly on my Radeon 9800 using the fglrx drivers (version '8.28.8').

Do you get as bad performance in all hardware accelerated applications?

---

### Post by hizaguchi on 2006-12-11
> **manatawady said:**
> Hi there - 
i received a "new" radeon 1650 pro yesterday. After fiddling with installation and things like that i know the fgrlx is running.

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series Generic
OpenGL version string: 2.0.6174 (8.31.5)



Is that based on the 200m chipset, like the X1100 is?  If so, the OpenGL implementation is severely broken and you're probably just screwed like me. :???:

---

### Post by chadk on 2006-12-11
Dropped my ATI for an nVidia.  Much better now.

---

### Post by marcele on 2006-12-11
I also own an ATI product (x200m in my laptop unfortunately). 

The problems are incredible!

1. There are no working opengl drivers for the x200m and edgy. The default ATI and Radeon drivers don't support opengl for the x200m and the last working fglrx drivers that supported opengl and the x200m are not supported under edgy. (And yes I have tried 8.28 and the latest from ATI's site and tried all the sideport bios changes). Edgy will hard lock within 30 seconds of boot with opengl enabled.

2. I am not able to run my second monitor (22 inch LCD) at its native resolution.

a. If I use big-desktop there is a bug where your mouse pointer gets misaligned on your main screen.
b. If I use xinerama instead of big-desktop there is another bug and the mouse pointer turns into a little blob of the first monitor when I have the mouse pointer on the second screen.

Both of these bugs have been in the unofficial bug tracker for almost a year and yet they still haven't been fixed by ATI yet. These x200m's are in thousands and thousands of laptops from major vendors like HP. 

Just read this story and more importantly the comments below:
[http://www.digg.com/tech_news/ATI_s_Market_Share_Is_Falling](http://www.digg.com/tech_news/ATI_s_Market_Share_Is_Falling)

The unfortunate thing is that this is going to be a major problem for ubuntu. When Mark Shuttleworth states that with future versions that they are going to "beautify" ubuntu (I think by adding in all the latest opengl goodies) what is going to happen to all the ATI users out there with no opengl? I would say this to Mark. If ATI isn't going to support their own customers , then its time to drop some cash and do it for them. Add opengl support to the default open source drivers and let everyone partake in all the opengl goodness.

Will I ever buy an ATI product again ? Nope. You don't piss off the nerds! We will have the last laugh :)

---

### Post by manatawady on 2006-12-11
thanks for ur replies.
the chipset is 530 afaik so it should be supported with the latest driver - think its the first driver to support this card.

Maybe the "newer" chipsets are causing trouble or are not really implemented well... could be but dunno 4 sure

---

### Post by Perfect Storm on 2006-12-12
Well, as the situation is at the moment: If you want serious gaming on linux, go for Nvidia card and Nvidia binary driver.

---

### Post by QOLIM on 2006-12-23
> **Artificial Intelligence said:**
> Well, as the situation is at the moment: If you want serious gaming on linux, go for Nvidia card and Nvidia binary driver.

couldn't agree more,

I got 2 pc's with ubuntu, 1 with an nvidia and 1 with an ati card.

I used to have windows on the ati-pc, and since I'm on linux i've had had lots oftrouble with getting the drivers to work.
And now, they work but in games I have like 1/4 of the fps I had in windows

On the Nvidia-pc (dualboot ubuntu windows64) I didn't have trouble installin gdrivers.   Just downloaded installer, installed and voila
and fps is just fine

---

### Post by Patrick-Ruff on 2006-12-23
kinda sad that it has come to that.  I'm in the process of setting up FGLRX again, after my attempted adventures in AIGLX, that failed, miserably.  the open source drivers are even worse . . . so I guess no Beryl for me till' I get a new laptop, or ATI stops this crap.

---

