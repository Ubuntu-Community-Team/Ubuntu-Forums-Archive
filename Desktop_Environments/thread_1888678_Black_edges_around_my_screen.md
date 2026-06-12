---
title: "Black edges around my screen"
date: 2011-11-29
forum: Desktop Environments
---

### Post by Clayf700 on 2011-11-29
Hey guys, So I previously had Ubuntu on my PC until I broke it so I re-installed it, and this time I have the annoying black edges around the screen. You know, and the content is sort of like zoomed in. It was normal for the first boot, but then some driver came along and it got the edges next time I booted it up.

My video card is an AMD Radeon 6700 HD series.
Ubuntu 11.10, 64-Bit
Any help is appreciated.

---

### Post by typhoon_tip on 2011-11-29
Using Gnome 3 or Unity ? If is the first one, forget about ATI with Gnome 3, is not compatible.

---

### Post by Clayf700 on 2011-11-29
> **typhoon_tip said:**
> Using Gnome 3 or Unity ? If is the first one, forget about ATI with Gnome 3, is not compatible.
Unity Luckily

---

### Post by typhoon_tip on 2011-11-29
> **Clayf700 said:**
> Unity Luckily

Loll ok :D Post one screenshot to me please, I can help with ATI.

---

### Post by Clayf700 on 2011-11-29
> **typhoon_tip said:**
> Loll ok :D Post one screenshot to me please, I can help with ATI.

Well, you see. The problem is, is that it stays at the same resolution (1920x1080) but it's sort of zoomed in to the screen (Thus making the black edges) and making it sort of fuzzy.

On my Windows 7 Partition I can adjust how zoomed in it is with the "AMD VISION Engine Control Center" Then adjust the percentage it is zoomed in.
Is there anything like that for unity?

---

### Post by typhoon_tip on 2011-11-29
There is, but it should be disabled by default. What is your monitor maximum resolution ? I still suspect something may not have been set correctly for your video card xorg.conf file.

Edit: sorry, I forgot to mention where is, it is in Compiz. You need to enable ccsm first
```
sudo apt-get install compizconfig-settings-manager
```

Then run
```
ccsm
```

That setting is on the Enhanced Coom Desktop plugin. You can enable the zoom feature by setting the hotkeys for it.

---

### Post by typhoon_tip on 2011-11-29
Anyway, before attempting the zoom fix, I would see if it is really using the max resolution. You can try to adjust the resolution not with AMD CCC but with Screen settings under System Settings.

---

### Post by Clayf700 on 2011-11-29
> **typhoon_tip said:**
> Anyway, before attempting the zoom fix, I would see if it is really using the max resolution. You can try to adjust the resolution not with AMD CCC but with Screen settings under System Settings.
Yeah, I'm Pretty Sure. It's at 1920x1080 With my Windows 7 and Mac OS X Partitions. I Looked at the resolution on my Ubuntu and it said 1920x1080.
btw is Compiz safe to use? It's the reason my Ubuntu broke the last time and I had to re-install it.
Thanks a ton!

---

### Post by typhoon_tip on 2011-11-29
> **Clayf700 said:**
> Yeah, I'm Pretty Sure. It's at 1920x1080 With my Windows 7 and Mac OS X Partitions. I Looked at the resolution on my Ubuntu and it said 1920x1080.
btw is Compiz safe to use? It's the reason my Ubuntu broke the last time and I had to re-install it.
Thanks a ton!

No, compiz-config is not safe at all with Unity loll But there is a way of getting back everything without reinstall.

Just remember if your Unity disappear, you have several options of resetting it before resorting to re-installation, easiest of all:

```
unity --reset
```

If it doesn't come back, you can still open a terminal and run ccsm from the terminal, find Unity plugin (usually disabled for some unknown conflict reason...) and tick it back, everything will be restored.

I wouldn't tweak that part anyway for the zoom problem. I think you have a multi-boot configuration on that machine, so please try this: shutdown the computer, wait for 20 seconds and start up directly in Ubuntu, see what happens.

---

### Post by Clayf700 on 2011-11-29
> **typhoon_tip said:**
> No, compiz-config is not safe at all with Unity loll But there is a way of getting back everything without reinstall.

Just remember if your Unity disappear, you have several options of resetting it before resorting to re-installation, easiest of all:

```
unity --reset
```

If it doesn't come back, you can still open a terminal and run ccsm from the terminal, find Unity plugin (usually disabled for some unknown conflict reason...) and tick it back, everything will be restored.

I wouldn't tweak that part anyway for the zoom problem. I think you have a multi-boot configuration on that machine, so please try this: shutdown the computer, wait for 20 seconds and start up directly in Ubuntu, see what happens.

Thanks man, very good to know. I'll try it out. Thanks a bunch!

---

