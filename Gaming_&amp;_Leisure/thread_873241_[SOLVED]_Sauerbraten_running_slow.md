---
title: "[SOLVED] Sauerbraten running slow"
date: 2008-07-28
forum: Gaming &amp; Leisure
---

### Post by 67GTA on 2008-07-28
I couldn't get more than 5-10fps and almost unplayable. I went in to the options and changed a lot of medium graphics settings to low, and got about 30fps. It plays better now until something explodes(barrels, rockets,grenades, etc). Then the fps will drop to 10 or below, and the game freezes for about 20-30 seconds. What other settings can I tweak to keep this from happening. I know I'm missing something simple:confused: I running HP laptop with AMD x2 2000MHz, and Nvidia 7150(256MB) with restricted driver.

---

### Post by r0b0t1 on 2008-07-28
Is your computer obviously not the gaming type? Because the only thing may be to upgrade hardware. Give us your specs?

---

### Post by 67GTA on 2008-07-28
I disabled the "soft explosions" option, and it is pretty smooth now. This isn't a high end machine, but it should run decent. 

HP dv6815nr laptop
Dual AMD Turion(tm) 64 X2 Mobile Technology TL-60 (2000.00MHz each)
3049MB RAM
GeForce 7150M / nForce 630M/PCI/SSE2/3DNOW! (256MB)
Nvidia MPC67 chipset

---

### Post by r0b0t1 on 2008-07-28
Ah, thats kind of odd. It seems like it should run it fine. I'm not an expert, do they have a page that is about the game being slow?

---

### Post by 67GTA on 2008-07-28
I looked on the sauerbraten forums. There are a lot of hackers and hacks there, but I don't want to get into editing files. I lowered several graphics settings and it isn't freezing anymore.

---

### Post by bellboa45 on 2009-02-20
How is this solved? I'm having much the same problem. The frame-rate doesn't go much higher than 10 FPS. It's so choppy I could barely get through the menu to turn all the video settings down. My computer isn't top of the line but it should do I think. P4-2.4Ghz, 1GB of RAM, 128MB ATI Radeon. Any ideas on how to improve my fame-rate? Thanks -Bryan S.

---

### Post by noerrorsfound on 2009-02-20
> **bellboa45 said:**
> 128MB ATI Radeon
1. Do you have the official drivers from ATI installed? Ubuntu should have prompted when you first installed about proprietary drivers or restricted hardware support.

2. The most important piece of information you should give for the video card is the name/model of it (for NVIDIA, an example would be an "8800 GT"). The amount of video memory and the name of the series (which Wikipedia says started in 2000) doesn't tell much about it. ATI's video cards are very poor for gaming on Linux, but they still should be able to run it at low settings, but not always. I recall that when I had an old ATI Radeon 9250 128mb card, I couldn't play Sauerbraten at all because the game would slow down to a crawl after the game was open for a few seconds.

[http://cubeengine.com/forum.php4](http://cubeengine.com/forum.php4) would get you better answers than here, since that's the official forum for the game and any players who resolved your problem will be there, as well as the main programmer himself.

(An additional suggestion for the future if you upgrade your video card: Choose NVIDIA if you plan on playing games on Linux.)

---

### Post by honeybear on 2010-12-12
> **noerrorsfound said:**
> 1. Do you have the official drivers from ATI installed? Ubuntu should have prompted when you first installed about proprietary drivers or restricted hardware support.

2. The most important piece of information you should give for the video card is the name/model of it (for NVIDIA, an example would be an "8800 GT"). The amount of video memory and the name of the series (which Wikipedia says started in 2000) doesn't tell much about it. ATI's video cards are very poor for gaming on Linux, but they still should be able to run it at low settings, but not always. I recall that when I had an old ATI Radeon 9250 128mb card, I couldn't play Sauerbraten at all because the game would slow down to a crawl after the game was open for a few seconds.

[http://cubeengine.com/forum.php4](http://cubeengine.com/forum.php4) would get you better answers than here, since that's the official forum for the game and any players who resolved your problem will be there, as well as the main programmer himself.

(An additional suggestion for the future if you upgrade your video card: Choose NVIDIA if you plan on playing games on Linux.)



have u tried to reduce the video depth and so on?


```

-d

This starts as a dedicated server. The default is a non-dedicated server with only a single client in graphical mode. Dedicated servers run in the shell only (no graphics), with increased priority yet use very little cpu time and memory, so you can run one in the background, or at the same time with a client if you want to host a game (which is usually better than using a listen server). Servers use the ports 28785 (UDP) and 28786 (UDP).

-dN

If N=1, starts a listen server which allows it to simultaneously function as both a client and server. Note that a listen server is limited by your in-game frame rate, so you should use a dedicated server if your graphics card is slow or you have enabled frame rate limiting options such as "vsync". If N=2, it starts a dedicated server as for the "-d" command-line option.

-wN

Sets the screen resolution width to N (default: 640).

-hN

Sets the screen resolution height to N (default: 480).

-bN

Sets the screen depth to N bits per pixel.

-zN

Sets the z-buffer precision to N bits. This should be at least 24 or you may experience depth problems.

-aN

Sets FSAA (Full Scene AntiAliasing) to N samples, i.e. -a4 is 4xFSAA

-vN

Sets v-sync to N (N=1 to enable or N=0 to disable).

-sN

Sets stencil buffer bits to N (N>=1 to enable or N=0 to disable).

-t

Sets Sauerbaten to run windowed.

-f

-fN

```

---

