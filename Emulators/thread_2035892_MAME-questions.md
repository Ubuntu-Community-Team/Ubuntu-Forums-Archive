---
title: "MAME-questions"
date: 2012-07-31
forum: Emulators
---

### Post by ZarathustraDK on 2012-07-31
So, I'm building my own arcade-cabinet to run MAME on, and I have a couple of questions I'd love to have answered:

1. Is the MAME-package in the Ubuntu-repos MAME or SDLmame? I think I read something about the 2 projects melting together, but I just had to make sure. Most MAME-resources I can find are from around 2007-2008, so I'm quite confuzzled as to what's supposed to be the bees knees nowadays.

2. How would you, in (Ubuntu)software, restrict a 24" widescreen monitor to a 4:3 aspect (effectively rendering the sides of the monitor black all the time, while keeping the 4:3 image centered). Asking because I intend to cover the monitor in a bezel so only an approx. 21" 4:3 screen remains. Sounds stupid, then check the prizes on 21 inch 4:3 LCD's ;)

3. Is there a GLSL-shader out there that mimics a CRT-screen? And will it work with 2).

4. Single-core, dual-core or quad-core processor, the Net doesn't seem to agree, but then again a lot of those discussions were from 2008.

Cheers ;)

---

### Post by nll on 2012-08-04
1- It's SDLMAME AFAIK. I don't know about the two projects merging.
2- MAME has a built-in option for that, keepaspect, which will keep the 4:3 ratio.
3- Check [this post]("http://ubuntuforums.org/showpost.php?p=12150013&postcount=4"). Yes, it works on all ratios, but it's very CPU intensive - 4:3 is faster.
4- The more, the better. =)

---

### Post by nll on 2012-08-04
Oops, I guess it really is MAME, not SDLMAME: [https://launchpad.net/ubuntu/+source/mame]("https://bugs.launchpad.net/ubuntu/+source/mame")

---

### Post by ZarathustraDK on 2012-08-10
Thanks for the reply ^^

The keepaspect function sounds nice (actually I think it's enabled by default for MAME).
The problem is when I inevitably have to drop out of MAME and its frontend to fix things in the system itself, like adding/removing roms, fiddle with artwork and the likes. Then a lot of the screen will be covered by the bezel of the cabinet.
Does Ubuntu have a kind of keepaspect function also? Given the constraints a 24" 1080p widescreen just begs to be run at 1280x1024 for a nice fit without any stretching.

---

### Post by nll on 2012-08-11
My laptop has a 16:9 screen running with a resolution of 1366x768, but in Unity's System Settings > Monitors > Resolution I still have the option of running it as a 4:3 screen with a resolution of 1024x768. The screen gets centered and unstretched with black sidelines. I think that's what you're looking for! =)

---

