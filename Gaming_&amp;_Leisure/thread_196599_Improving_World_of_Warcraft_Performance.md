---
title: "Improving World of Warcraft Performance?"
date: 2006-06-14
forum: Gaming &amp; Leisure
---

### Post by shirt on 2006-06-14
I recently got WoW up and running on my machine, however, it lags a considerable amount. Normally I would just deal with it, but the video lag is so bad that every time I try to turn my character it creeps along at a lethargic pace. Here is some background information: I'm using an ATI Radeon (9500 if i remember correctly) and I have all sound turned off and most graphical settings at their lowest. In Windows, the game ran great even with some of the graphical settings on, but in linux it is essentially unplayable. I have installed and checked to make sure the fglrx driver is working properly and I get around ~3000 fps when running glxgears. To cut this short, is there any way I can increase my performance so that I don't experience so much video slowdown?

---

### Post by GIBson3 on 2006-06-14
[QUOTE=shirt]I recently got WoW up and running on my machine, however, it lags a considerable amount. Normally I would just deal with it, but the video lag is so bad that every time I try to turn my character it creeps along at a lethargic pace. Here is some background information: I'm using an ATI Radeon (9500 if i remember correctly) and I have all sound turned off and most graphical settings at their lowest. In Windows, the game ran great even with some of the graphical settings on, but in linux it is essentially unplayable. I have installed and checked to make sure the fglrx driver is working properly and I get around ~3000 fps when running glxgears. To cut this short, is there any way I can increase my performance so that I don't experience so much video slowdown?[/QUOTE]

This is just a stab in the dark, but I'd blame ATI, their Linux drivers are not as good as NVidia's and under windows they've been known to have issues with WoW anyway.

Beyond that, what are your system specs, what "VM/ENU" are you using to run wow, also are you running Wow with the -opengl command line switch and or **SET gxApi "opengl"** line in the config.wtf file.

Beyond that I'm not sure, I'm running an ubuntu box at work for basic desktop use and I've gotten playable WoW preformance on a P3 1.0Ghz/512mb ram/GeForce 3 - 64meg  (Stormwind is about 12-15 fps, Elwynn Forest sees me around 17-20fps.

---

### Post by Montre on 2007-08-08
Also, Specs:
AMD 64 3200+
Ati X1600
2gb Ram


I suffer the same problem however I don't know why.

I grabbed the newest version of wine and installed it up. I then went through Ubuntu's restricted Driver manager and downloaded the newest ATI drivers for my X1600.

After that I installed WoW and Burning crusade and began tweaking. I made a registry entry for Opengl inside of wine that was suggested on another wiki thread designed to increase performance. After that I added did the Api "opengl" line in the config.wtf. and added -opengl to my launcher to ensure open gl was enabled.

In game I only see about 15-20 fps. I've been told plenty of places that I could witness the same performance as my Prev XP installation which saw upwards of 60fps and down to 40ish once I installed 50 mb or so of addons.

I'm getting 15-20 with NO addons just camping out in a corner of Shattrath. I hear ATI support for linux is lacking, but a friend of mine running Redhat sees the same performance as his XP install and hes often running another game in the background, switching in and out via Beryl.

Any suggestions?
I'm running the 64 bit v of linux as my processor's arch supports that. Wine didn't puke on install as I grabbed the 64 install. However could the drivers that installed via Restricted Driver Manager not be for 64 bit arch and I may see proper performance if I go to the ATI site and dl the Feisty 64 bit drivers?

On a gentoo installation guide for WoW they mentioned "unmasking" the video card and setting its archectecture to the systems archectecture. Hrmmm, I don't think ubuntu supports this as the commands in terminal fail.

May just repartition and make an XP installation for WoW, but then I could have problems with Grub.Arrrgh!

---

### Post by Montre on 2007-08-08
Also, to anyone else who finds this thread via the search utility. This thread has a fix for some ATI issues. This MAY or MAYNOT help you. I don't know. I haven't tried it yet as I'm at work, but a few posts down its mentioned in a link:

[http://ubuntuforums.org/showthread.php?t=519751](http://ubuntuforums.org/showthread.php?t=519751)

It might help someone with a similar problem if they find this thread :)

---

