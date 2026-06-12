---
title: "Unity launcher text popup bug/bad rendering"
date: 2012-08-19
forum: Desktop Environments
---

### Post by Ema TheMirror on 2012-08-19
Hello,

I installed Ubuntu 12.04 64-bit yesterday. Sadly, I just noticed that when I hover my mouse on the launcher icons up and down, along the launcher, the text popup arrow displaying the name of the icon's program is often badly rendered, looking like a shadow or a broken popup. It's not just a matter of speed, if I leave the cursor over the icon, the text popup remains glitchy.

I have to say it looks bad, very unpolished, and I hope there's a way to have it fixed. I know it's fairly a cosmetic bug, but it's really disappointing and glitchy, not to mention Rhythmbox hiding the bottom end of the song's title because the font size is too big, but that's another story.

My PC is powered by an AMD Phenom quad-core CPU and ATI card. I've already installed proprietary ATI drivers, but it's not made any difference.

Ironically, if I take a screenshot of the broken onmouseover text popup, it first gets rendered correctly, then takes the shot.


[EDIT] I've seen that removing icons from the launcher so that it doesn't have to pile/expand them helps, since the text popup is displayed correctly. I think it has to do with the icon tiles animation

---

### Post by NadirPoint on 2012-08-19
I wonder if what you are seeing is related the thread I am about start.  Seems some type of news plugin has invaded my Unity pulldown menus rendering them and whatever application they overlay virtually useless.

---

### Post by Ema TheMirror on 2012-08-20
No, I don't think that's what I'm referring to.

To make things clearer I took a screenshot of the glitch. Physically, with my camera pointing to the screen, since a software "print button" screenshot doesn't show the glitch, as I mentioned in my previous post.


[IMG]https://fbcdn-sphotos-b-a.akamaihd.net/hphotos-ak-ash4/383808_3895871747774_1832393992_n.jpg[/IMG]

Moiré effect apart, you can clearly see that sometimes (quite often) the text arrow indicator turns into a shadow of itself - now it's just a grey line barely visible. It stayed there for all the time I could take out my camera and take the photo, so it's not just a matter of loading it.

That happens when the launcher's full of icons and piles them up... the stack/expand animation is smooth and really wonderful, but it leads to those glitches. I've noticed that with less icons in their fixed position (no need to stack/expand them) the indicator works fine.

---

### Post by bastones on 2012-08-20
I'm getting the exact same issue - I think after applying the latest update a few days ago. It happened on my desktop PC (Acer Aspire M1930) and also happens on my laptop (Lenovo B570e) - the latter with an Intel HD 3000 graphics card and desktop with an AMD Radeon 6xxx graphics card.

---

### Post by nehalem04 on 2012-08-21
Same problem here. I'm also using 12.04 64bit. At first I thought it was due to faulty driver from nvidia, but even after installing driver v.304.37 it still persists. I'm pretty sure it is due to some updates, because when I first installed(in April) 12.04 the problem wasn't there.

---

### Post by nehalem04 on 2012-08-21
This bug was submitted to launchpad. Apparently a compiz update issue. 
Follow the link below:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1037458](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1037458)

---

### Post by Destain on 2012-08-25
I have the exact same issue and I'm pretty sure as well this happened after some updates. I'm running the built in Intel Drivers
D

---

### Post by linuxguy049 on 2012-08-25
> **Destain said:**
> I have the exact same issue and I'm pretty sure as well this happened after some updates. I'm running the built in Intel Drivers
D


> after compiz 0.9.7.8 update

I'm getting this error too. Anyone know how to remove this update?

---

### Post by claracc on 2012-08-26
One of the ways to get a bug be fixed is to vote, "yes, this bug also affects me" in the addresed launchpad bug link: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1037458](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1037458)

---

