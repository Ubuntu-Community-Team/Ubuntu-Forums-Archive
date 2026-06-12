---
title: "Several questions regarding multiple monitor setups."
date: 2010-05-20
forum: Desktop Environments
---

### Post by undecim on 2010-05-20
I'm planning my next desktop build (currently only have a laptop that is falling apart), and one of the features I'm really looking forward to is multiple monitors. I'm thinking a 1920x1200 center monitor and two 1600x1200 on either side, but I'm not decided just yet. I don't know if I really need that resolution.

I have a few specific questions though. The only time I've ever messed with multiple monitors is way back when I had Windows, so I'm not sure what to expect on Ubuntu.

1: What is the best Graphics card brand/series to use? I've seen that ATI has more powerful hardware than nVidia for the same price range, but nVidia seems to support Linux better. I'm using an ATI card in my laptop now and have never had any problems with it (with either open source or proprietary drives, other than open source drivers didn't do well with 3d). I would also like these GPUs to be running F@H while I'm away, so GFLOPS is just important as gaming performance.

2: Since I want to use 3 monitors, I assume I should get 3 of the same graphics card or a card with 3 identical outputs (do those exist?).

Or can this be done some other way. For example, a more powerful card for the center monitor, and less powerful cards for the other two. Do those need to be the same brand, or could I use, for example, ATI and nVidia cards on the same desktop simultaneously?

3: Is it possible to have a virtual console on one monitor with a desktop on the other two, or do I need to set up a terminal on the desktop to use that monitor?

4: How can I run fullscreen SDL games with multiple monitors? Will it only show on one screen or stretch across them all? Is it possible to have a fullscreen game running on one monitor with the desktop visible on the others? How would the mouse focus work with that? Or does it just all depend on how I setup the monitors?

Any other advice you have is appreciated as well.

Thanks in advance!

---

### Post by portentum on 2010-05-20
> **undecim said:**
> 
1: What is the best Graphics card brand/series to use? I've seen that ATI has more powerful hardware than nVidia for the same price range, but nVidia seems to support Linux better. I'm using an ATI card in my laptop now and have never had any problems with it (with either open source or proprietary drives, other than open source drivers didn't do well with 3d). I would also like these GPUs to be running F@H while I'm away, so GFLOPS is just important as gaming performance.


1: If you're going to be playing games nvidia is what I'd recommend. I can't point to a particular card, I'd just say go with what you can afford. I'm very happy with my GT 220. I'll be comfortable telling people to buy ATI cards again when I stop seeing complaints on just about every wine entry about this or that ATI card. :?

> **undecim said:**
> 
2: Since I want to use 3 monitors, I assume I should get 3 of the same graphics card or a card with 3 identical outputs (do those exist?).

Or can this be done some other way. For example, a more powerful card for the center monitor, and less powerful cards for the other two. Do those need to be the same brand, or could I use, for example, ATI and nVidia cards on the same desktop simultaneously?


2: I don't know of any three output cards off the top of my head. You can use a powerful card for the center, and a cheaper card for the other two though, yes. I'd stick with the same brand for consistency, but the same card isn't necessary.

> **undecim said:**
> 
3: Is it possible to have a virtual console on one monitor with a desktop on the other two, or do I need to set up a terminal on the desktop to use that monitor?


3: Unfortunately I don't know of a way to have only a terminal running on one monitor with an X server on another. Except maybe to just start an X server and run a single terminal application full screen on it. I'm not ruling it out as impossible, if I do that someone else will come along and say "nuh uh! Here's how" and explain it. Hopefully that person wanders along and explains anyway, because I'd be very interested in this myself.

> **undecim said:**
> 

4: How can I run fullscreen SDL games with multiple monitors? Will it only show on one screen or stretch across them all? Is it possible to have a fullscreen game running on one monitor with the desktop visible on the others? How would the mouse focus work with that? Or does it just all depend on how I setup the monitors?

4: There are a number of ways to set up multiple monitors. I'm sure one of them involves a fullscreen game being stretched over multiple displays, but mine doesn't. I typically have a fullscreen smplayer playing movies or tvtime for TV on one of my monitors while I have a game on the other. I have separate X Servers for each monitor, so the mouse is the only thing that moves between them. Otherwise, they're isolated. Can't drag applications from one to the other or stretch them across two. There are setups that do allow this, they just aren't to my liking.
Games can and will grab your mouse to prevent leaving the screen if they're the type (FPS, for instance) that needs it to stay there.

I may have missed a point or two, but hopefully others will weigh in on this anyway and give some more perspectives. Hope this helps.

---

### Post by Nythain on 2010-05-20
the only thing i could really add to this is i would personally have the more powerful card running two monitors, since its going to be doing more work theoretically. not sure how much of that would rely on the gpu vs cpu though.

---

