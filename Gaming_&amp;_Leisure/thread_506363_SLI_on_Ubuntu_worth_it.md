---
title: "SLI on Ubuntu worth it?"
date: 2007-07-21
forum: Gaming &amp; Leisure
---

### Post by Snipersnest on 2007-07-21
I'm guessing this is the place to post this question since its the gaming area.
 
I'm wondering if people have had decent results with SLI on Ubuntu gaming for games like World of Warcraft and Counter-Strike Source.
 
If you guys could post most a bit on your FPS and stuff that'd be great.
 
SLI wasn't supported in Linux when I built this system so I've only setup one card with Ubuntu before. I have **two BFG Geforce 6800 GT OCs** that I run SLI via Windows right now. So my question is simple.
 
**Is SLI in Ubuntu worth it, is it a headache, and do you get decent enough results?**

---

### Post by shad0w_walker on 2007-07-22
Assuming you have drivers with SLi support installed its a snap to setup. Try using this command:

```
sudo nvidia-xconfig --sli=auto
```

That should add in the SLi option to your xorg.conf file, reboot your xserver and you should be good to go. I have a pair of 7600GTs in my system right now and it seems to work just fine.

---

### Post by weblordpepe on 2007-07-22
Owned.

---

### Post by Nkari on 2007-07-23
oooh, gotta run that command, I have a couple of 7600s in my machine, I know they are both working at the very least as Separate cards, just don't know if they are SLIing at the moment or how to even test for that.

SO I think that just answered my question.

Now if only I could get WoW to work properly under ubuntu, (my current very bad work-around is to use windows), I could tell you what sort of improvement it did or didn't make in games like WoW.

---

### Post by Snipersnest on 2007-07-23
> **Nkari said:**
> oooh, gotta run that command, I have a couple of 7600s in my machine, I know they are both working at the very least as Separate cards, just don't know if they are SLIing at the moment or how to even test for that.
 
SO I think that just answered my question.
 
Now if only I could get WoW to work properly under ubuntu, (my current very bad work-around is to use windows), I could tell you what sort of improvement it did or didn't make in games like WoW.
 
If you need help getting WoW to run please let me know.. I can help you with that part :D

---

### Post by Nkari on 2007-07-23
Do you want me to Hijack this thread with the wow problems or would you prefer a new one?

---

### Post by Snipersnest on 2007-07-23
Its up to you honestly.. it would still relate if your going to test it on SLI settings :)

---

### Post by Nkari on 2007-07-23
True, it is the perfect testbed for your query. Toggle the SLI on and off look at the relative FPS and there is your instant answer.

I'm not at home at the moment, so nowhere near that computer, however there is some extended outputs from what is seen on the command line posted in the Screenshot and open WoW thread, as well as my WTF file contents.

Basically the problem is if I try to start it with GL mode forced (either through the WTF or the switch on command line) it tells me that my video card is not supported and I need one with Dual TMU support. 

If don't force GL (guess that is D3D mode) I can log in and select my character but as soon as I try to enter the world it freezes or if I go to character creation and try to change race or class it freezes, changing facial features, skin colours etc does not make it freeze up.

---

### Post by Yabbo on 2008-05-30
Give us some specs Im running WOW on my ubuntu 7.10 system... you need to have the restricted drivers installed and be running the current version of wine. and follow these instructions...
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

It worked perfect for me :)

---

