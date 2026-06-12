---
title: "Weird visual glitches with Windows games"
date: 2012-12-18
forum: Gaming &amp; Leisure
---

### Post by szczurcio on 2012-12-18
Hi,
First, I'm rather new to Ubuntu (installed it like 3 days ago?). Anyway, I thought it would be nice to play some good old titles which, unfortunately, support nothing but Windows. The solution - Wine. Sure. I've installed COD MW1 and MW2 so far, and both run nice apart from a weird visual glitch - instead of smoke/fog effects, I get a weird... surface, flashing red/black/whatever. This happens just with smoke or mist effects, although I suspect it might affect the general game performance as it sometimes skips, which, considering the configuration of my computer, should not happen. But anyway, I have updated the drivers already (card: GeForce GTX260), which indeed helped (games looked like in thermal vision before I did that, no colors), but something is still missing, I guess. Any ideas? I'm afraid to tamper with drivers on my own, already broke the system this way.

Thanks in advance.

---

### Post by mastablasta on 2012-12-18
windows games are best played in their native system
 
if you do it in wine you first check for any specific patches or tips& tricks to get them running porpperly on wine applicaiton database.
 
next ubuntu uses 3D desktop with special effects by default. it can interfere with games running in wine(or at least it used to as i rember). KDE (Kubuntu) has a neat feature that turn off all desktop effects when you run some full screen programmes. you could also try with a window manager (for example the quite light icewm) and see if glitches appear there as well.
 
if you are using 12.04 verison you oculd try using unity 2D or classic gnome panel. they are both 2D by default i believe.

---

### Post by szczurcio on 2012-12-18
Ok I did update the drivers to the very latest version, still nothing though. And I can't switch to 2D, it's removed in 12.10. Any ideas? I have DirectX9, but maybe that's not enough, am I missing something?

---

### Post by oldrocker99 on 2012-12-18
Did you just use wine to install your game, or did you try PlayOnLinux? POL has a bunch of prebuilt scripts which will get many, many Windows games running. Try removing your .wine/whateverthegameis folder, install PlayOnLinux (available from [http://playonlinux.com](http://playonlinux.com) for free, of course), and try installing using PlayOnLinux. Its scripts know about installing Microsoft dependencies in order for a game to run.

It's certainly worth a try. I just don't know which game you meant (COD?).

---

### Post by szczurcio on 2012-12-19
I meant Call of Duty MW 1 and 2. And yes, I did try POL, but it's exactly the same.

---

### Post by holastickboy on 2012-12-19
Here are the results of other players using MW2 on Linux (perhaps you can have a look at their notes and see if there is anything that you need to change?)
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=10600](http://appdb.winehq.org/objectManager.php?sClass=application&iId=10600)

---

### Post by szczurcio on 2012-12-20
Quote from the test of the latest version:

Graphical glitches everywhere (Shaders bug). Interesting to note that it  works fine on 1.3.2x series, but not from 1.3.3x-1.4 series. Something  is severely broken there.

And below, in a comment:

This game needs 
winetricks strictdrawordering=enabled 

That will solve the graphical glitches that many are seeing.

Which, in my case, worked. So far so good ;), so if anyone is facing this problem, I think it's worth a try. And holastickboy - thanks a lot.

---

