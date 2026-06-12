---
title: "glxgears is wrong?"
date: 2005-01-30
forum: Gaming &amp; Leisure
---

### Post by crazypenguin on 2005-01-30
14599 frames in 5.0 seconds = 2919.800 FPS
14249 frames in 5.0 seconds = 2849.800 FPS
13967 frames in 5.0 seconds = 2793.400 FPS
16537 frames in 5.0 seconds = 3307.400 FPS
16144 frames in 5.0 seconds = 3228.800 FPS
16212 frames in 5.0 seconds = 3242.400 FPS



I have a geforce4mx440
that doesn't happen with a geforce4mx440

---

### Post by jensyt on 2005-01-30
[QUOTE=crazypenguin]14599 frames in 5.0 seconds = 2919.800 FPS
14249 frames in 5.0 seconds = 2849.800 FPS
13967 frames in 5.0 seconds = 2793.400 FPS
16537 frames in 5.0 seconds = 3307.400 FPS
16144 frames in 5.0 seconds = 3228.800 FPS
16212 frames in 5.0 seconds = 3242.400 FPS



I have a geforce4mx440
that doesn't happen with a geforce4mx440[/QUOTE]
I'm not sure what the problem is... Is this above or below your expectations? I get about the same with my Radeon 9800 Pro, but I'm not complaining. :D

Also, glxgears is not very good for benchmarking, or so I'm told.

---

### Post by Moobert on 2005-01-30
yeah you can get high numbers like that if anything is clovering the glxgears render window. Thus it has less to render and you get more fps. I have a geforce 4 mx 420 and get about 1100. also installing the newer nvidia drivers from their site, if you have the ones with warty (6111, i think) will give about a 10% fps gain in glxgears.

---

### Post by daniels on 2005-01-30
glxgears is not a useful benchmark.

---

### Post by valadil on 2005-01-30
That doesn't sound too terribly wrong.  I used to get 1500-3000 out of a GeForce2.  Then again one of my sutiemates can barely get 500 out of a GeForce5200.  What does this mean?  That glxgears is not a good benchmark, of course.

---

### Post by crazypenguin on 2005-01-30
The thing is, i normally get ~400.
I'm thinking it was the window-coverage-thing

---

### Post by daniels on 2005-01-30
Yes, if your window isn't mapped, then the entire thing will get optimised away, and never rendered.  But anyway, the reason glxgears is not a benchmark is because games do not consist of three solid-fill textures with a single light source.  If you like to watch solid gears spinning, and can tell the difference in how fast they spin, great.  The only halfway useful benchmark is what you use: if you bought a card to play HalfLife 2, then compare how well it goes in HalfLife 2, not how well it does something that was quite exceptionally low-tech many generations of cards ago.  It's a useful benchmark for one thing: is DRI working at a very basic level?

---

### Post by dhonn on 2005-02-02
[QUOTE=valadil]That doesn't sound too terribly wrong.  I used to get 1500-3000 out of a GeForce2.  Then again one of my sutiemates can barely get 500 out of a GeForce5200.  What does this mean?  That glxgears is not a good benchmark, of course.[/QUOTE]

It means he probably didnt install his nvidia drivers right. ** Driver "nvidia"** instead of **Driver "nv"** in /etc/X11/xorg.conf after you install the nvidia drivers.  Also restart xserver ctl+alt+bkspace or reboot.

---

### Post by ladoga on 2005-02-02
I get 85.0fps in glxgears, also same in every game using 9800pro.

Reason: vsynch and hsynch on. no ripping. Screen at 85Hz ofcourse. Without vsych you'll just skip frames, tear frames etc. as your screen and fps are out of synch.

---

### Post by valadil on 2005-02-02
[QUOTE=dhonn]It means he probably didnt install his nvidia drivers right. ** Driver "nvidia"** instead of **Driver "nv"** in /etc/X11/xorg.conf after you install the nvidia drivers.  Also restart xserver ctl+alt+bkspace or reboot.[/QUOTE]

Nope.  I went through nvidia stuff for him (not that he messed anything up, but I'm more concerned with video stuff than anyone else in the suite so he had me double check).  We think it's because other than the video card he's got the sketchiest hardware you can imagine.  On his previous vid card the monitor would click when windows were dragged.  Monitors don't click.

---

