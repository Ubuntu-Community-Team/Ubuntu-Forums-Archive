---
title: "No screensaver with Beryl on Edgy"
date: 2007-02-26
forum: Desktop Environments
---

### Post by FuturePilot on 2007-02-26
I'm running Beryl on Edgy and when the screensaver comes on, I only get a blank screen. Any way to get the screensaver running with Beryl?

---

### Post by shareMenaPeace on 2007-02-26
For me i get random crashed when i use screensaver at all. I use currently 1 screensaver which only crashed once yet (last 3 days)  And what have you set rightnow as screensaver? Maybe the current screensaver is to much, change it to see if another works.

---

### Post by rainwalker on 2007-02-26
I have the same problem, my screensaver is set as Flurry but it never comes up. I'm not positive, but I think there were times before I installed Beryl (which I did a couple of days ago) when the screensaver wouldn't show up, so maybe it's an Ubuntu thing?

---

### Post by FuturePilot on 2007-02-26
None of them work. I have it set for Stonerview and I also tried others, but I always get a blank screen.

---

### Post by kristinc on 2007-02-27
I can't help, but I can say that I have exactly the same problem as the topic starter:

Beryl runs smoothly and nice with the flappy windoweffects and all things fancy. When I run the metacity window manager instead of Beryl, the screensavers run smoothly and nice. But I can't get the **3D** screensavers to work with Beryl - only the **2D** ones show up while the others are displayed as a black screen. This goes for both fullscreen and preview. Glxgears is also extremely choppy with Beryl - oh, and Totem crashes when I try to play a movie clip. I have an Nvidia GeForce4 420 Go card on my laptop, a fast enough Intel Celeron 2.2 GHz processor, and I should mention I've seen this work nicely on an older and slower stationary PC.

Anyways, I'll be sure to post a solution if I find it (I'll look over at the Beryl forums). Hopefully things will get better with Feisty.

[SIZE="1"](I know an obvious solution is to forget the fancy screensavers alltogether and run blank screen, but I'm a real sucker for nice graphics, even when it's totally unnecessary.)[/SIZE] :rolleyes:

---

### Post by steveneddy on 2007-03-03
If you install xscreensaver, all will be well. gnome-screensaver doesn't like beryl for some reason. After install, type 

```
xscreensaver-demo
```

to select your wild screensavers.

Cheers - SE

---

### Post by rainwalker on 2007-03-04
> riley@Riley:~$ xscreensaver-demo
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
*********************************WARN_ONCE*********************************
File radeon_mm.c function radeon_mm_alloc line 216
Ran out of GART memory!
Please consider adjusting GARTSize option.
***************************************************************************
Error: Could not get dma buffer... exiting

What does this mean? The "Screensaver Preferences (XScreenSaver 4.24, 21-Oct-2005)" window comes up and I chose "Only One Screensaver" for the Mode, and when I clicked "Flurry", the preview showed for 1 or 2 seconds, then disappeared and said "No Preview Available". If I click on another screensaver, it might or might not show the preview for that one, then if I click back on Flurry, it might or might not show it then too. If I quit the window and lock my screen, the screensaver still doesn't show up. 
Not only that, but the Flurry in that window looks a lot cooler than the one in the Metacity screensaver window, it has multiple flurries sometimes.

---

### Post by steveneddy on 2007-03-11
I don't know that much about the radeon cards, being an nVidia customer myself.

---

### Post by isecore on 2007-03-11
I'm running Beryl 0.2 from the SVN repos and I had this problem as well. I'm running on a Nvidia GFX5600 and every time the screensaver kicked in everything just stopped with a black screen. Only way to get back was to ctrl-alt-backspace and kill X. I also had an extremely annoying problem where gksudo would only display a gray screen and thusly add some noise to an otherwise lovely Ubuntu experience.

However, after some fiddling around and experimenting with the Beryl-settings I discovered that if I unchecked "Unredirect Fullscreen Windows" in General Options - Main - Advanced these problems went away. Check that option and the problems came back.

So give that a try and see if it solves your problems.

---

### Post by FuturePilot on 2007-03-11
Thanks I'll give that a try.:)

---

### Post by Contrast on 2007-04-01
> **steveneddy said:**
> If you install xscreensaver, all will be well. gnome-screensaver doesn't like beryl for some reason. After install, type 

```
xscreensaver-demo
```

to select your wild screensavers.

Cheers - SE

Thanks a lot. This worked for me on a Feisty install; I'm assuming it would've done the same had I tried it when I was having the same problem on Edgy.

---

### Post by ChameleonDave on 2007-04-19
> **steveneddy said:**
> If you install xscreensaver, all will be well. gnome-screensaver doesn't like beryl for some reason. After install, type 

```
xscreensaver-demo
```

to select your wild screensavers.

Cheers - SE

Aha!  Thanks!

I was having trouble with screensavers on PCLinuxOS (running KDE) after installing Beryl, but xscreensaver has fixed the problem.  Thanks again.

---

