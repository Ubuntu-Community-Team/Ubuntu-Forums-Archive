---
title: "Why moving windows with compiz isn't smooth?"
date: 2009-03-31
forum: Desktop Environments
---

### Post by Joe_Bishop on 2009-03-31
Moving them with metacity is smooth, as well as moving with kwin and windows. As I remember, this issue appeared in beta or alpha of 8.04 and my 7600gt, but still here with beta of 9.04 and 8800gtx.
What is it?

---

### Post by ScottDeagan on 2013-01-17
This reply is a little late, but I feel this post is worth commenting on  as it's now 2013 and dragging windows around on Ubuntu 12.10 still  isn't perfectly smooth. I'm OCD about this issue, so every time I see  janking/stammer/stutter, it drives my nerves crazy. I have a desktop,  and an nVidia GTX 460 and an AMD Radeon 7870. I use the latest  proprietary drivers for each (310.19 on nVidia and Catalyst 12.11 beta  on AMD). This is what I have found:

1. Dragging a window near the top of the screen or the Unity launcher results is stutter.
2. If Firefox (version 18) is open with a JavaScript game open, dragging windows is stuttery.
3. Playing a video results in stuttery window dragging.

I've tried all sorts of things to try and fix this, including:

1. Turning on "tear free" option in the Catalyst driver.
2. Ensuring "sync to vblank" is enabled in CCSM.
3. Manually setting the refresh rate in CCSM.
4. Setting "CLUTTER_PAINT=disable-clipped-redraws:disable-culling" in /etc/environment.
(etc etc etc).

I've  tried so many things I can't even remember now. Nothing has worked.  Sometimes dragging windows is super smooth, then it'll just start  stuttering a couple of seconds later.

Because the same thing was  happening with both the AMD and nVidia cards, I just assumed there was  something wrong with Compiz. Then, something extraordinary happened. I  got a new laptop with a integrated graphics - the Intel HD 4000. I  thought I'd give Linux another try, installed Ubuntu 12.10, and to my  surprise everything just worked!!! Well, I tell a lie, I have to change  the Intel's HD 4000 acceleration scheme from UXA to SNA, and in order  for this to work I needed to install the edgers PPA and update xorg.  However, even running in the default UXA mode, dragging windows was  perfectly smooth. What also works perfectly is dual monitor support. I  plugged in a secondary monitor into the mini DisplayPort, and it just  worked.

I have found that while dragging windows around is  perfectly smooth, with two monitors running (1080p and 1440p), the HD  4000 struggles with a couple of the Compiz effects. For example, the  SuperKey + W (to show all open windows) stutters when I have both  monitors plugged in. However, with a single monitor, even at 2560 x  1440, it's buttery smooth. It's so "pixel perfect" that I want to kiss  my screen. There may be a workaround, but I haven't seen any posts from  anyone suffering from the same issues (it may not annoy most Linux user  using dual monitors).

While the Intel HD 4000 is an integrated  GPU and cannot push the same number of pixels as current dedicated GPUs,  I have found that the Intel HD 4000 works best with Linux (I treasure a  smooth and fluid desktop, free of stutter - I don't do much gaming,  just QuakeLive, which the Intel HD 4000 handles effortlessly). I'm going  to get an Intel motherboard and a core i7 for my desktop PC.

---

### Post by grahammechanical on 2013-01-18
Wow, you must be OCD if you searched for a post that is not far from being 4 years old! Why did you not just open a new thread?

I advise that when buying a new motherboard you be careful about Nvidia Optimus technology. Nvidia is yet to provide a driver for it and the open source driver is slowly, slowly getting to grips with Optimus.

[http://bumblebee-project.org/]("http://bumblebee-project.org/")

I think that many of us do not understand the difficulty that Linux developers have in keeping up with advances in hardware when they receive so little (often, no) support from the hardware manufacturers. We blame the distribution when the failure lies with the manufacturer not supporting Linux as well as they should. Or, at all in many cases.

Regards.

---

