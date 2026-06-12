---
title: "Kwin or compiz = periodic 3D frame drop?"
date: 2011-03-17
forum: Desktop Environments
---

### Post by RobbieThe1st on 2011-03-17
I've got a small problem. I've got the FurMark benchmark running through Wine. It's a very good GPU stressing program, and works very well through Wine - As good as native performance, seemingly.
That being said, I'm running into some odd issues with it, and with any other heavy 3D program:
I'm getting periodic frame-drops. Of course, the more GPU-heavy it is, the more it stands out - with glxgears the stuttering is barely noticeable.
To see what I mean, watch this short video: [http://robbiethe1st.afraid.org/images/linux/20110317_002.mp4](http://robbiethe1st.afraid.org/images/linux/20110317_002.mp4)
As you can see in the video, I -don't- get the drops with both window managers disabled - Which means that it has something to do with either kwin or compiz. Oh, and just so you know - Compositing -is- disabled in kwin.

What's going on here?

My specs:
Kubuntu 10.10 x86_64, uname -a: "Linux rb-dt-kub1010 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64 GNU/Linux"
Processor: 3.5ghz Phenom II x4
Ram: 4GB DDR3 1600
Video card: GTX 260 216-core; Nvidia stock drivers(270.30 - Note: I tried a number of different drivers without any real effect; this one seems to be as stable as they get).
PSU: Corsair 750W - We aren't getting any problems from this.
Temps: Under max load, the CPU's under 50C, Northbridge under 55C, and GPU under 70C - well under any limits.

I assume we've got something polling or blocking the CPU for a slight fraction of a second, but I've no real clue - How should I go about troubleshooting this?

---

### Post by RobbieThe1st on 2011-03-18
*sigh* Noone has -any- clue? wow.

---

