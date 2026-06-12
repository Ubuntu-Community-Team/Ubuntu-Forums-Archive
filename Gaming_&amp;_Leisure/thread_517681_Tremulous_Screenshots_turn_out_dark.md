---
title: "Tremulous Screenshots turn out dark"
date: 2007-08-04
forum: Gaming &amp; Leisure
---

### Post by fatsheep on 2007-08-04
I have run '/bind F2 screenshotjpeg' in the tremulous console to take screenshots by pushing F2.  When I press F2, a screenshot is taken in ~/.tremulous/base/screenshots, HOWEVER, these screenshots are quite dim.  I have tried restoring them with GIMP but it ruins the quality of the image...  In order to play Tremulous, I have to turn up the brightness all the way or the maps are just too dark.  The screenshots look like I have the brightness turned all the way down (screenshot below).  Is anyone else running into this problem?

[[IMG]http://img358.imageshack.us/img358/1016/shot0008yj3yo5.th.jpg[/IMG]](http://img358.imageshack.us/my.php?image=shot0008yj3yo5.jpg)

---

### Post by fatsheep on 2007-08-05
Well I know there are Tremulous players here.  If you play Tremulous, please do me a little favor and take a few screenshots and then go to ~/.tremulous/base/screenshots and see if they turned out dark like mine or not.  

By the way, in order to take screenshots in tremulous hit the ` key (right above the tab key) to open the console (or possibly Shift + ` which would normally produce the ~ character).  Then type '/bind <KEY> screenshotjpeg' without quotes and hit enter.  I use F2 for my key.

Thanks,

- fatsheep

---

### Post by DoktorSeven on 2007-08-05
I don't play Tremulous, but I get the same thing in a few other games as well.  It's like the game doesn't take into account its gamma/brightness settings when creating a screenshot.

Unfortunately the only thing I've been able to do is do as you did, brighten them with Gimp.  Careful manipulation helps with not ruining the quality, but of course it's not quite the same as what you originally saw.  I think it's up to the devs to find a fix.

---

### Post by fatsheep on 2007-08-05
> **DoktorSeven said:**
> I don't play Tremulous, but I get the same thing in a few other games as well.  It's like the game doesn't take into account its gamma/brightness settings when creating a screenshot.

Unfortunately the only thing I've been able to do is do as you did, brighten them with Gimp.  Careful manipulation helps with not ruining the quality, but of course it's not quite the same as what you originally saw.  I think it's up to the devs to find a fix.

Yea, unfortunately this problem is larger than I thought.  I rigged a bash script to run the "scrot" command every 10 seconds while I was playing the game.  Well, it worked but the screenshots were just as dark which means the problem is most likely not limited to the Tremulous screenshot utility. :(

---

### Post by hikaricore on 2007-08-05
You did originally tell us that you turn the brightness all the way up when playing.
Could this by any chance be a brightness/contrast issue on your monitor?

Post up a few shots that are "too dark" and let a few others give their opinions on the matter.

If they're anything like the one you posted at the top, then I don't see the problem as it looks fine.

---

### Post by fatsheep on 2007-08-06
> **hikaricore said:**
> You did originally tell us that you turn the brightness all the way up when playing.
Could this by any chance be a brightness/contrast issue on your monitor?

Post up a few shots that are "too dark" and let a few others give their opinions on the matter.

If they're anything like the one you posted at the top, then I don't see the problem as it looks fine.

Here's another one.  I think Tremulous is just a dark game...  There's probably nothing wrong.  However, this is ALOT darker then it appears ingame.

[[IMG]http://img410.imageshack.us/img410/7115/shot0170we6.th.jpg[/IMG]](http://img410.imageshack.us/my.php?image=shot0170we6.jpg)

---

### Post by alterpinguin on 2007-08-06
please check the ioquake forums about it - there are some changes on the way too.  - The problem is turning up the brightness is like turning up the brightness of your monitor, it never has any effect to the color-values of the textures ingame. I did not try the tremulous screenshot feature, but this is what happens in other quake-like games too (quake3, ioquake, enemy-territory, ...) - so the game can only  recalc settings, which are changed by itself and have to do the whole recalculation (time-dependant) and even then may be wrong. Next, for your own experience, you should compare same pictures on a flatscreen and on a tubescreen - they will look very different in most times.

---

### Post by fatsheep on 2007-08-06
> **alterpinguin said:**
> **please check the ioquake forums about it - there are some changes on the way too.**  - The problem is turning up the brightness is like turning up the brightness of your monitor, it never has any effect to the color-values of the textures ingame. I did not try the tremulous screenshot feature, but this is what happens in other quake-like games too (quake3, ioquake, enemy-territory, ...) - so the game can only  recalc settings, which are changed by itself and have to do the whole recalculation (time-dependant) and even then may be wrong. Next, for your own experience, you should compare same pictures on a flatscreen and on a tubescreen - they will look very different in most times.

That's good to hear. :)  I will check.

---

### Post by Lord Illidan on 2007-08-06
I have the same problem. Trem plays very dark on my pc..have to turn the gamma all the way up.

---

