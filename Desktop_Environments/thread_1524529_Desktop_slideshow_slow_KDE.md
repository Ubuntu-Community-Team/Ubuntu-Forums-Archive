---
title: "Desktop slideshow slow KDE"
date: 2010-07-05
forum: Desktop Environments
---

### Post by jbo5112 on 2010-07-05
I'm running a slideshow for my background in KDE, but I had to boost the time from a few minutes to a few hours.  Every time it switches my computer comes to a near halt until it is done.  Even DVD playback drops to around 1 fps for a few seconds seconds, when I can even see the desktop.

I'm running KDE 4.4.2 with compiz at 1920x1440 on a 3.4 GHz Core 2 Quad, w/ 6GB RAM and a GeForce 8600 GT.  The system should be able to handle the load.  Even if it is slow, it shouldn't halt a quad core.  By comparison, I have a simple single-threaded slideshow program that I wrote, which can zip through the images at 15+ fps while scaling them to full screen.

---

### Post by ankspo71 on 2010-07-05
Hi,
I have this problem too but not as severe. When I run 'top' in the terminal and manaually change the wallpaper, I can see Xorg jump up to as high as 55% cpu. I think the problem has to do with kwin's compositing, because I can suspend compositing (or disable all 3d effects) and make the problem disappear. 

This isn't a fix but it should help the performance out alot.
Try adjusting the graphics effects quality by going to: 
Settings > System Settings > Appearance > Style > Fine Tuning;
Then change graphical effects to --> "low display resolution and low cpu". 
It makes a big difference on my computer.
Hope that helps.

---

### Post by lkjoel on 2010-07-05
> **jbo5112 said:**
> I'm running a slideshow for my background in KDE, but I had to boost the time from a few minutes to a few hours.  Every time it switches my computer comes to a near halt until it is done.  Even DVD playback drops to around 1 fps for a few seconds seconds, when I can even see the desktop.

I'm running KDE 4.4.2 with compiz at 1920x1440 on a 3.4 GHz Core 2 Quad, w/ 6GB RAM and a GeForce 8600 GT.  The system should be able to handle the load.  Even if it is slow, it shouldn't halt a quad core.  By comparison, I have a simple single-threaded slideshow program that I wrote, which can zip through the images at 15+ fps while scaling them to full screen.
Hmm, I have KDE 4 with compiz at 1200*1100 (i think) on a Pentinum III, w/ 2.9GB RAM, and an old video card.
I have everything working properly.

Try this:
```
sudo apt-get update
sudo apt-get upgrade
```

---

