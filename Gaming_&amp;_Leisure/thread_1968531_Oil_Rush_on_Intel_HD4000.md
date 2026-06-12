---
title: "Oil Rush on Intel HD4000"
date: 2012-04-29
forum: Gaming &amp; Leisure
---

### Post by Carborundum on 2012-04-29
I intend to purchase a new computer in the near future, on which I am planning to do some light gaming.

For the processor I am considering the recently released Intel Ivy Bridge, mostly due to the updated graphics specifications. My hope is that the HD4000 chip will be powerful enough to handle all titles currently available on Linux, at least on lower settings. 

One of the games I am interested in playing is Unigine Corp's *Oil Rush*. However, the system requirements mention "HD3000 (Windows or Mac only)", and a quick search seems to confirm that the game does not run well on Sandy Bridge graphics under Linux.

Now, the HD4000 is quite a bit more powerful than the HD3000, and it is my understanding that the support for both Sandy and Ivy Bridge graphics have been greatly improved between kernel 3.0 and 3.2. I am wondering if anyone has any experience running Oil Rush on Ivy Bridge graphics, and could tell me if the performance is acceptable?

---

### Post by cRaZyBisCuiT on 2012-05-10
Hi Carborundum,

I'm sorry that I don't have any experiences with the HD4000. But I expect the HD4000 should be able to let you play OilRush in Linux, it got a 20-30% better performance than the HD3000.

But very new hardware doesn't run that smoothly in linux mostly. So I guess with 2-4 kernel updates the performance and the possible bugs will get better or entirely fixed. But that's just an expectation.

Cheers,

cRaZy

---

### Post by hero1900 on 2012-05-10
try to ask this question on oilrush forum. they will help you out i am very sure

---

### Post by Loïc2 on 2012-05-13
The problem with the Intel graphics is the Linux drivers. Mesa is still stuck at OpenGL 3.0 series, 4 years old, when we've had 3.1, 3.2, 3.3, 4.0, 4.1, 4.2 already. [[COLOR="Red"]3.1 isn't even coming this year[/COLOR]]("http://www.phoronix.com/scan.php?page=news_item&px=MTA5Njc")... Also see [http://www.phoronix.com/scan.php?page=news_item&px=MTA5NzM](http://www.phoronix.com/scan.php?page=news_item&px=MTA5NzM)

Even OpenGL 3.0 isn't enough for recent games, as far as I remember Oil Rush is build for 3.3 or 3.2 at least (for lowest quality graphics), and 4.X for better graphics. Even though they've been fixing things here and there to make the game sort of half work on open drivers, they can't make miracles.

And Oil Rush doesn't even use the advanced effects in their Unigine engine, which means even if you managed to get the game kinda work, you couldn't expect it for future games based on that engine. And with a few other engines starting to consider Linux versions, you'd also be setting you up for not being able to play future Linux games. For example, I don't think Valve is really considering open source drivers in their Linux ports (LFD2, etc...), every one porting advanced engine for Linux are still stuck with the proprietary drivers. Same for Kicstarter 3D games coming to Linux.

If you're purchasing a desktop computer, you can go with the Intel processors and add a low end AMD or Nvidia graphics card later. If you're considering a laptop though, and if you really need integrated graphics, the AMD processors are a far better choice. Though the open source ones still aren't on par with Intel's for other features, you get the possibility to run every game with the Catalyst drivers, which support all recent OpenGL versions and offer far better performance than the Intel ones. The power consumption is on par with Intel's nowadays, and the processor is hardly the limiting factor. The AMD APU would make a world of difference for any 3D game.

---

