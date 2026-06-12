---
title: "Lag in Dota 2 with 120fps"
date: 2013-12-02
forum: Gaming &amp; Leisure
---

### Post by ruddi on 2013-12-02
So I was just wondering if you guys could help me figure out why I am lagging even though I get constant 120 fps in game? 
It's not because of my internet connection because this happens also when I am playing against bots.
Yes I have tried different drivers but nothing changes, constant 120fps but still lag.
All my other games run smooth (metro, l4d2, tf2)

Would be cool if Dota 2 would work then I could delete my windows partition :)

System:
Ubuntu 13.10
i7 3770K 
gtx 760 nvidia 331.20
16gb of ram

---

### Post by dannyboy79 on 2013-12-02
are you sure it's lag? lag is latency in my book. is there any graphics settings you can change like turning on v-sync, anti-alising, and other stuff like that. maybe if you could record it using kazam or simplescreenrecorder and then upload it to youtube (marked as unlisted) and then paste the link here we can see what you're experiencing.

---

### Post by ruddi on 2013-12-02
Thank you, I will do that as soon as I am home from work :)

---

### Post by ruddi on 2013-12-02
Here is the link [COLOR=#666666][FONT=arial] [/FONT][/COLOR][http://youtu.be/FMEb8Okd35k](http://youtu.be/FMEb8Okd35k)
This is with all settings at default, vsync is on and everything else maxed out, I have tried changing the settings but with no luck.

---

### Post by cRaZyBisCuiT on 2013-12-03
So you tried disabling VSYNC in the game and also in the nvidia-settings? Maybe that could save you some headache. But still I should mention I have the same issue with my 560ti. I get constant 50fps+ but sometimes the game stucks for a nanosecond. I believe it's a bug. Dota on linux is already playing quite nicely but has some (most of them) minor bugs.

EDIT: I just watched your video. It seems like vsync is turned on. If not ingame, then in the driver. Try to disable it (it's named "sync to vblack" or something like that). At least that should boost your fps. In addition: You don't get constant 120 FPS but 60 FPS which also indicates VSYNC trouble.

---

### Post by Arthur_D on 2013-12-03
crazybiscuit: you know how vsync works, right? Unless there is a serious driver bug with it, it will not cause a game to visibly lag.

---

### Post by cRaZyBisCuiT on 2013-12-03
No, that's true. VSYNC normaly will try to synchronize the FPS output with the monitors refresh rate. But e.g. if the pc is to slow to provide 60 FPS, the frames will drop to 30 (or even 15). This kind of lag would be visibly then. In case the performance is always good enough to provide 60fps (for 60 Hz tft) there SHOULD be no problem.

Disabling AA and VSYNC can sometimes prevent this kind of lags though it's not a general performance problem but a performance peak problem, if you want to call it so.

---

### Post by Arthur_D on 2013-12-03
I've never seen it try to sync to anything less than the monitor refresh rate - if it gets under 60 FPS, it still renders at 40, 50 or whatever else it gets at the moment. Curious to know where you have that from - not implying you're deliberately lying, but I've never heard (nor seen) it implemented like that.

---

### Post by ruddi on 2013-12-03
Yes the video is with vsync on, with vsync of in compiz, nvidia and the game there is not difference but I get 120 fps(the game can only go to 120fps) but like I said, there is no difference with the performance when vsync is off, the only difference is that I get crazy tearing.
So is the game just buggy or is there something else I can try? :)

---

### Post by dannyboy79 on 2013-12-03
it shouldn't matter when you have a GTX 760 (powerhouse of a graphics card) but try to turn compositing off. no compiz at all.

---

### Post by ruddi on 2013-12-03
Turned compositing off, no noticable change when vsync was on but with vsync on the game was unplayable

---

### Post by dannyboy79 on 2013-12-03
> **ruddi said:**
> Turned compositing off, no noticable change when vsync was on but with vsync on the game was unplayablei didn't mean just shut it off, i meant at your login greeter, choose Unity 2D, is that an option?

although, if your other games play fine than possibly it's just something with this game and the version of the drivers you're using. For example: i can't use the AMD Catalyst 13.4 drivers and play Serious Sam 3 BFE, it actually locks up my entire machine and I can't even access tty1 sessions. I switched to AMD Catalyst 13.11 V9.4 and all is well. So sometimes it's just a particular combination of hardware and drivers and a certain game that something is just not right. I can't explain it otherwise.

---

### Post by pnarciso on 2013-12-04
Dota 2 stutters a lot especially while panning through the map with vsync enabled. If I disabled it I get 120 fps constant and no stuttering.

---

