---
title: "Why is compiz so slow in natty?"
date: 2011-05-04
forum: Desktop Environments
---

### Post by screaminj3sus on 2011-05-04
I am dual booting natty and linux mint debian edition. I have noticed in LMDE compiz is far, far, far, far smoother. In natty scrolling, resizing, and animations are all noticeably laggier. In LMDE I can use the normal resize with no problem, in natty its so laggy I need to use rectangle or stretch. Animations are also glitchy (fade animations have white flicker) In lmde there are no visual hiccups.

I am using the same driver and kernel in LMDE, the major difference is LMDE has a much older compiz (0.8.4, before the compiz++ rewrite I believe.) Does anyone know why the newer compiz in natty is so much slower? Does anyone else expereince this? my video card is an hd2600 using the cat 11.4 driver, but I experience these same issues with the oss driver.

---

### Post by deconstrained on 2011-05-04
What you should try first is adjusting Compiz's referesh rate. It should be the same rate as that of your monitor to get best results. When I upgraded to Natty I had the same problem; the refresh rate was reset to 50 instead of kept at 60 where I had set it previously. However, although readjusting the refresh rate vastly improved its performance, Compiz was still a bit sluggish when paired with Unity.

---

### Post by screaminj3sus on 2011-05-04
yep forgot to mention in both natty and mint I unchecked sync to vblank in compiz, and set my refresh rate to 60. (I have tear free desktop enabled in cat as well, but turning that off doesn't help things either)

---

### Post by deconstrained on 2011-05-04
Try selecting "Ubuntu Classic" as your default session at the login screen, or install Debian then?

I decided to stick with plain old Gnome and gnome-do/run dialogue (which can practically read my mind already), so to get things quickly I don't need a cumbersome menu at the side that takes more than three seconds to go to the bottom of.

---

### Post by screaminj3sus on 2011-05-04
Yeah speed issues are the same in classic as well, it seems for some reason natty's compiz is just really, really slow.

---

### Post by screaminj3sus on 2011-05-05
well this is rather bizarre. I changed the theme from the default ambiance to elementary.

It fixed almost every problems. No more white flickers, firefox scrolling way smoother. (resize is still unusable with normal though)

Is the default theme just that unoptimized?

Scrolling in firefox is now the smoothest its ever been in linux

---

### Post by reader4 on 2011-05-17
I'm seeing slower response in both unity and classic modes as well with compiz on.  Changing themes did not help for me.  Adjusting the refresh rate may have helped a little, but not much.  Here is an ad-hoc test: when I click the Firefox launch icon with compiz enabled, the window takes about 1-2s to draw on the screen.  With metacity enabled, the window draws in less than 1s and feels almost instantaneous.  Same with XFCE.  The machine is a dual Xeon 3.4 GHz (from 2005) with 128MB nVidia Quadro FX 1400 and 4GB RAM and nvidia drivers installed (v185).

---

### Post by screaminj3sus on 2011-05-26
From my testing it seems to be a problem with both light-themes (for some setups) and the version of compiz in natty (there is a bug report in for light themes, this doesn't seem to effect all cards, mostly nvidia. The light themes thing didn't seem to effect my intel card)

today I downgraded my compiz using this:[http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html](http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html)

to compiz 0.8.6. Every is smoother, much less buggy. I went from not being able to use normal window resize at all, to it working flawlessly. Scrolling is smoother as well. This version also included the minimize effect plugin which I find far smoother than the buggy animations plugin.

This is on a different laptop then my op, I now have an intel card, and natty's default compiz was still craptastic.

Something really needs to be done about this by 11.10... older versions of compiz, gnome shell, and kwin run a lot smoother than natty's compiz on this card.

---

### Post by wildmanne39 on 2011-05-27
> **screaminj3sus said:**
> I am dual booting natty and linux mint debian edition. I have noticed in LMDE compiz is far, far, far, far smoother. In natty scrolling, resizing, and animations are all noticeably laggier. In LMDE I can use the normal resize with no problem, in natty its so laggy I need to use rectangle or stretch. Animations are also glitchy (fade animations have white flicker) In lmde there are no visual hiccups.

I am using the same driver and kernel in LMDE, the major difference is LMDE has a much older compiz (0.8.4, before the compiz++ rewrite I believe.) Does anyone know why the newer compiz in natty is so much slower? Does anyone else expereince this? my video card is an hd2600 using the cat 11.4 driver, but I experience these same issues with the oss driver.
Hi, I had issues with compiz but I set the cube up and adjusted several settings and now it work great. I used this guide to set up the cube in natty and that is when I made the other adjustments as well. [http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)  I also had that vsync in 2 places one in compiz and one in my nvidia settings.

---

