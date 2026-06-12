---
title: "Black windows with visual effects"
date: 2010-01-27
forum: Desktop Environments
---

### Post by easyfit on 2010-01-27
Hello

I've got sort of a special setup with an Ubuntu box with a Nvidia Quadro Plex (4 DVI out) connected to a 4K-projector (4 DVI in).

The setup basically acts like 2 Quadro 5800 cards connected to 4 seperate screens which are then joined together in a 2 x 2 grid with Nvidias Mosaic feature. So I'm getting a unified 4096x2160 display.

Anyhow, I've got all of that working, but the problem is that whenever I drag a window out to be a certain size on the desktop (close to the full size of the desktop) it just turns black. If I then resize the windows to be a little smaller again, then it displays just like it should.

Even when the windows are black their applications still seem to function normally and I still see tooltips and right-click-menus and so on.

If I turn visual effects off, this problem goes away as well. And I should also mention that I'm getting exactly the same thing in KDE, so I'm guessing it has something to do with X or Nvidias drivers.

Could this be some sort of memory issue? Could I be filling up some sort of buffer when I make the windows to be almost the size of the entire screen? And are there any such prarameters I could try tweaking to fix this?

I realize it's not your everyday problem, but any help/input would be much appreciated.

---

### Post by warfacegod on 2010-01-27
I'm no expert on this but it sounds like your simply asking too much of your graphics cards. When I'm running Compiz and want to watch a video in Fullscreen, I have get a similar issue. My graphics card can't handle video larger than a certain size + Compiz at the same time so the video stalls until Compiz is turned off.

Try temporarily disabling one or two screens to see if the issue goes away.

---

### Post by easyfit on 2010-01-28
Is that with an Nvidia card as well?

I doubt it's because of lacking hardware that it does this... because if it were the GPU that's being pushed too hard it would just run a bit slower, and I doubt it's running out of memory either with the amount of memory being available on todays graphics cards.

So I'm guessing it's probably some sort of bug in Nvidias driver... which means there's probably not much I can do :/

---

### Post by warfacegod on 2010-01-28
> **easyfit said:**
> Is that with an Nvidia card as well?

I doubt it's because of lacking hardware that it does this... because if it were the GPU that's being pushed too hard it would just run a bit slower, and I doubt it's running out of memory either with the amount of memory being available on todays graphics cards.

So I'm guessing it's probably some sort of bug in Nvidias driver... which means there's probably not much I can do :/

Yes it's nVidia. Geforce Go5200 64 MB. Only a very few custom effects running and fullscreen will bring it to it's knees. For me to run a second Monitor from my laptop, the effects *must* be off.

Although running Compiz takes *allot* of video resources, having just looked at your card specs on nVidia's site, I'm not so sure horsepower is the issue. Are you certain you are using the proper drivers?

---

### Post by warfacegod on 2010-01-28
Maybe this will help:

[http://ubuntuforums.org/showthread.php?t=884161&highlight=GeForce+7600+GS]("http://ubuntuforums.org/showthread.php?t=884161&highlight=GeForce+7600+GS")

---

### Post by easyfit on 2010-01-29
Hello again

I've fixed the issue simply by updating to the latest Nvidia drivers rather than the ones given by Ubuntu. So it really was a bug in the drivers. Everything works great now, full visual effects running smoothly over a 4096x2160 screen :)

Thanks for taking an interest though warfacegod.

---

### Post by warfacegod on 2010-01-29
Sure, no problem. Don't forget to mark as solved under thread tools.

---

