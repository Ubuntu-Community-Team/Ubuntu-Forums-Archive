---
title: "Morrowind: have you managed to run it? If so, what is your hardware config?"
date: 2006-09-10
forum: Gaming &amp; Leisure
---

### Post by ZylGadis on 2006-09-10
I've tried to run Morrowind a few times with no success. Today I decided to investigate why some people (me included) have a certain problem, while others play it freely. Since I only have one type of hardware configuration, I ask people with different hardware (or even the same, if that is possible) who have managed to run the game to share their experiences here, with the hope that we can resolve the situation.

Here it goes:
I have a NVidia 5200, and an Nvidia 6200 (in a different box). I use Dapper on both boxes.
There are generally two ways to run Morrowind with wine: either install it in Windows, copy the files over to Linux and add a few .dlls, or use a wonderful Loki installer that does that for you ([http://www.liflg.org](http://www.liflg.org))
No matter which way I go, I have the same experience. The launcher splash screen with the Options, Data Files, etc menu starts and works great. When I start the game itself, though - either by clicking on Play in the launcher splash screen or by typing "morrowind" (which does "wine Morrowind.exe"), the console spits a few hundred of warning messages (which is quite normal with wine and usually has no effect on the program), then a small  320x240 window shows up, and immediately another, smaller error window shows on top of it, stating "Render Creation Error: Unknown stencil mode format."
I have tried all kinds of configurations of wine and/or Morrowind (pixel shaders on/off, etc). The only change to the above that I have encountered (i.e. it produces a different error message at the same point) is if I manually go into the wine registry and change Morrowind's screen depth to 24 bits - the default is 32. Then the game complains that it must run in 32 bit depth.
So far, so good. Indeed, my Xorg runs in 24bit depth. I tried to push it to run in 32bit, and it crashed, telling me that my hardware does not support that.
After a bit of googling through nvidia forums, I came across the following:
[http://www.nvnews.net/vbulletin/showthread.php?t=17543]("http://www.nvnews.net/vbulletin/showthread.php?t=17543")

It seems I have a problem with the bit depth - the nvidia driver for linux does not support 32bits. The last 8 bits are only used for alpha (i.e. transparency) anyway, so you don't need them much. Morrowind, though, uses a lot of transparent overlays. It is my suspicion that my 24bit depth is the reason for the Uknown stencil mode format error, and I cannot change that to 32 because of the Nvidia driver.

Is there someone who can report running Morrowind successfully in Linux with an Nvidia?
I know there are people here who enjoy playing the game in Linux - for example, AI. Can you please post your hardware configuration and, in particular, graphics card, graphics driver, and screen resolution and depth?
Thanks.

P.S. If someone is interested, I can post a screenshot with the "Unknown stencil mode format" message.

---

### Post by leech on 2006-09-10
It ran for me, I was going to just say use the installer from liflg.org, but apparently you're already aware of that.  

I also have an nVidia card (6800GT).  It could be that newer versions of Wine have broken it.  I had tried it in both Cedega and with the liflg.org installer.  They both had their share of bugs, so I didn't play it much.  Then of course Oblivion came out, and I started playing that in Windows.  But then again, Morrowind I completed (the original, not the expansions), yet I kind of lost interest in Oblivion.  One day I'll pick it up again, perhaps.  Same as Morrowind, I'd like to give the Tribunal and Blood Moon a try.

Leech

---

### Post by Carbon Based on 2006-09-11
I installed morrowind with the liflg.org installer. I got the same error in wine as the first poster. So I installed CVSCedega, everything up to the main menu was fine, although the opening "Bethesda" animation was extremely slow. Once everything loaded (.esm files etc.) the game exited before displaying the menu with a "cannot display filter graph" error or something similar. From searching around I've found that this is a common problem with cvscedega and morrowind. I'd be interested in anyone's experience running Morrowind on regular Cedega, especially on older hardware, as I'm using Ubuntu on a laptop with an older Radeon graphics card that is unsupported by the linux fglrx radeon drivers.

---

### Post by Eanas on 2010-05-24
when i go to synaptic and i search wine and try to install it come a error could not mark all package for installation or upgrade........................................... pleas can you help

---

