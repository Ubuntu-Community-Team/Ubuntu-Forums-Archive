---
title: "How do I get SDL to use the SVGALIB driver?"
date: 2012-04-27
forum: Gaming &amp; Leisure
---

### Post by kerryhall on 2012-04-27
I built chocolate doom from source on a machine that is not running X. Chocolate doom uses SDL only AFAIK, but of course SDL can use various drivers. I tried to launch chocolate doom and it looks like it's trying to use DirectFB as the driver, but getting:

opening '/dev/fb0' and '/dev/fb/0' failed. 

I would rather just use the svgalib driver, since I can compile and run svgalib apps on this box just fine. 

How do I set SDL to use the svgalib driver? Thanks!!

---

### Post by The Rnegade on 2012-05-01
> **kerryhall said:**
> I built chocolate doom from source on a machine that is not running X. Chocolate doom uses SDL only AFAIK, but of course SDL can use various drivers. I tried to launch chocolate doom and it looks like it's trying to use DirectFB as the driver, but getting:

opening '/dev/fb0' and '/dev/fb/0' failed. 

I would rather just use the svgalib driver, since I can compile and run svgalib apps on this box just fine. 

How do I set SDL to use the svgalib driver? Thanks!!

not to question your skills, but are you sure youre using sdl audio? Sdl sound is supposed to let you're audio manager pick the driver. maybe you should make sure all your sdl libs are installed and up to date. this could be a problem from missing the necessary libraries

---

### Post by kerryhall on 2012-05-02
Thanks for replying! SVGALIB is a video driver, I'm not concerned about audio in this case.

---

### Post by kerryhall on 2012-05-03
Any ideas here?

---

### Post by kerryhall on 2012-05-07
Still wondering...

---

### Post by Sslaxx on 2012-05-08
Why on earth do you want to? Why are you not running X? SVGALIB hasn't been updated much since 1999.

---

### Post by kerryhall on 2012-05-08
Hmmm good question. The game would probably run faster if it was ported to use SVGALIB directly :P

Basically, I have some older machines that I want to repurpose as gaming machines, and would rather not incur the overhead of X. (Although I do realize the overhead usually comes from gnome, not X)

Because it would be fun? Is that a good reason? :)

---

### Post by kerryhall on 2012-05-09
I think "for fun" is a valid reason, as this IS in the gaming subforum :)

---

### Post by mode7 on 2012-05-10
Make sure you have SDL compiled with svgalib support:
```
./configure --enable-video-svgalib
```
Then set env variable for SDL to use svgalib:
```
export SDL_VIDEODRIVER=svgalib
```

Just my guess. I have not tried personally. If it were me, I'd just use directfb, seems far more active. Or just go ahead and use X.

---

### Post by kerryhall on 2012-05-10
Hell yeah, that is sounding like what I need.

I'll give that a try. I tried grepping through the SDL headers but I realized I should try grepping through the SDL source! (duh!!)

And if I can't get that going, I'll give DirectFB a try.

Thanks!!

---

