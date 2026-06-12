---
title: "UT2004 Demo poor performance on Ati x1150"
date: 2007-08-12
forum: Gaming &amp; Leisure
---

### Post by Baby Boy on 2007-08-12
Hi. I installed UT2004 demo (natively) on my Dell Inspiron 1501 just to see what's it capable of. I was bitterly dissapointed.
The game runs like a slide-show even at the lowest setting, and I am sure it could do better. I know Ati is crappy for gaming in Linux and the x200m should be bad for OpenGL (my GPU is x1150 which should be about 30% faster) but it can't be this bad. I've installed the drivers via Restricted Driver Manager. 
So tell me, is there a way to improve this poor performance? Another set of drivers or something? I saw lots of people say this GPU is quite capable of playing games like UT2004.
Here is what I get when I type fglrxinfo
> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series
OpenGL version string: 2.0.6334 (8.34.8 )

My laptop specs are in my sig, as I said the GPU is Ati Radeon Xpress 1150  256MB HyperMemory.

---

### Post by Baby Boy on 2007-08-12
Bump

EDIT: Also, I am having the same problem as the guy in this thread [link]("http://ubuntuforums.org/showthread.php?t=500581&highlight=ati+x1150+driver+linux"), I don't know what to do :sad:.

---

### Post by coarse.sand on 2007-08-12
I've been using an Xpress 200m for about two years now. The 1150, as I understand it, is an upgraded version of the 200m, which is itself a mobile version of the Radeon X300 (has half the pipes or whatever). Now from reading about the 200m and its truly MASSIVE problems with OpenGL, the OpenGL issue lies with the chipset the X300 is actually based on. Since the 200m and 1150 derive from it, they too have some of the worst OpenGL support you'll ever see.

I own Unreal Tournament 2004, and I bought it specifically to have something to play on Linux. It is painful. Once you get out of the small deathmatch style maps, everything becomes a slideshow, even on the lowest of low settings. When you're getting 2-3 fps with a 200m, guess what? A 30% increase with the 1150 is still completely unplayable. These cards were really plainly made for a Windows based system running Direct3D, and ATI refuses to even support their cards, telling any one who owns one to go back and see the manufacturer for driver updates. It's a pity, especially if you want to run Linux, but I've learned my lesson from all of this, and the next time I buy a computer I'm only going to look at nVidia cards, and I suggest you do as well. ATI/AMD is probably going to be missing a big chunk of the market share in the future because these cards are in the laptops that college students are buying, and in just a few years they're going to be choosing to look elsewhere for graphics cards.

Anyways, since you cant get Unreal Tournament 2K4 working, I have some other suggestions. Both Warsow and Open Arena run fairly well, and I imagine Nexuiz might also be playable on low enough settings.You can also find other games that use OpenGL that your machine is still capable of running in a playable state, but anyone who told you UT2004 was capable of running with your card was playing it on Windows where it gets to use DirectX.

Edit: Worth mentioning because I just tried it: [Legends]("http://legendsthegame.net") is a Tribes clone done on the Torque engine, and I can report back that it runs at a perfectly decent clip on the 200m.

---

### Post by Baby Boy on 2007-08-13
> **coarse.sand said:**
> I've been using an Xpress 200m for about two years now. The 1150, as I understand it, is an upgraded version of the 200m, which is itself a mobile version of the Radeon X300 (has half the pipes or whatever). Now from reading about the 200m and its truly MASSIVE problems with OpenGL, the OpenGL issue lies with the chipset the X300 is actually based on. Since the 200m and 1150 derive from it, they too have some of the worst OpenGL support you'll ever see.

I own Unreal Tournament 2004, and I bought it specifically to have something to play on Linux. It is painful. Once you get out of the small deathmatch style maps, everything becomes a slideshow, even on the lowest of low settings. When you're getting 2-3 fps with a 200m, guess what? A 30% increase with the 1150 is still completely unplayable. These cards were really plainly made for a Windows based system running Direct3D, and ATI refuses to even support their cards, telling any one who owns one to go back and see the manufacturer for driver updates. It's a pity, especially if you want to run Linux, but I've learned my lesson from all of this, and the next time I buy a computer I'm only going to look at nVidia cards, and I suggest you do as well. ATI/AMD is probably going to be missing a big chunk of the market share in the future because these cards are in the laptops that college students are buying, and in just a few years they're going to be choosing to look elsewhere for graphics cards.

Anyways, since you cant get Unreal Tournament 2K4 working, I have some other suggestions. Both Warsow and Open Arena run fairly well, and I imagine Nexuiz might also be playable on low enough settings.You can also find other games that use OpenGL that your machine is still capable of running in a playable state, but anyone who told you UT2004 was capable of running with your card was playing it on Windows where it gets to use DirectX.

Edit: Worth mentioning because I just tried it: [Legends]("http://legendsthegame.net") is a Tribes clone done on the Torque engine, and I can report back that it runs at a perfectly decent clip on the 200m.
Just what I was afraid of. So there's no way around it, no driver update or anything? How about games in Wine or Cedega? Do they work well?

If that's it, OK, I'll just have to deal with it. UT2004 is really not my type of games, I just wanted to try how it works. I didn't buy this laptop for gaming, and I knew Ati has bad Linux support. Still, it's frustrating to know that I am using about 15% of my GPU's potential.

---

