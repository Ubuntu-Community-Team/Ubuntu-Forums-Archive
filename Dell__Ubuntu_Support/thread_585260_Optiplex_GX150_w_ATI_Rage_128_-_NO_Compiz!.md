---
title: "Optiplex GX150 w/ ATI Rage 128 - NO Compiz!?"
date: 2007-10-21
forum: Dell  Ubuntu Support
---

### Post by schagg on 2007-10-21
I just put 7.10 (gutsy) on a Optiplex GX150. Everything is stock except the video card. I just put in an ATI Rage 128.

For whatever reason, no matter what I do, I cannot get Compiz Fusion to actually run (work at all). I've tried all kinds of different guides. At this point, I'm not sure I have the right driver installed, although the install automatically recognizes the video card. So I thought that it would automatically install the correct one.

Could it be that the machine and card just don't have enough power to run Compiz? Below are some guides I've tried to follow. I've reached my limit on Linux knowledge, which isn't saying much since I'm a n00b when it comes to Linux


Tried:

http://forlong.blogage.de/"#blogentry_451

[https://ubuntu.com/ubguntu/desktopguide/C/hardware.html](https://ubuntu.com/ubguntu/desktopguide/C/hardware.html)

[https://help.ubuntu.com/community/CompositeManager](https://help.ubuntu.com/community/CompositeManager)

[http://ubuntuforums.org/showthread.php?t=536149](http://ubuntuforums.org/showthread.php?t=536149)


I'm willing to try just about anything. What should I try next?

---

### Post by schagg on 2007-10-21
Does anyone think this card would work? : 


[http://www.newegg.com/Product/Product.asp?Item=N82E16814121525](http://www.newegg.com/Product/Product.asp?Item=N82E16814121525)

---

### Post by strider_mt2k on 2008-01-01
I think the comparatively older 16MB card might simply not be up to the task.
If you can upgrade the card it's probably all you need to do.

I have a GX240 and got lucky in finding a 64MB half-height AGP card and it seems to run it all quite well.

---

### Post by bentheexo on 2008-01-03
that driver is in the system but you have to select it from the screens option when you change what type of monitor that you have installed

---

### Post by talkingwires on 2008-01-04
> **schagg said:**
> I just put 7.10 (gutsy) on a Optiplex GX150. Everything is stock except the video card. I just put in an ATI Rage 128.That's your problem right there. Like strider_mt2k mentioned, the ATI Rage 128 doesn't have the hardware needed to run Compiz. You'll need a card with hardware T&L in the GPU at minimum, with shader support for anything more than the basic effects. A GeForce 256 or Radeon 7000 would be the absolute minimum.

Take a look at this [list that ranks graphics cards]("http://www.overclock.net/graphics-cards-general/54675-graphics-card-ranking.html") by speed all the way back to the first generation. Anything under the Raedon 7000 lacks hardware T&L and will not run Compiz. Not that you need to buy the latest and greatest card to run Compiz. I'm running Compiz on my laptop with a Radeon 7500 (take a look how far the list *that* is) and everything is silky smooth.

---

