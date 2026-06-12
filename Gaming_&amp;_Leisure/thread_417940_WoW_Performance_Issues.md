---
title: "WoW Performance Issues"
date: 2007-04-22
forum: Gaming &amp; Leisure
---

### Post by thejayjay on 2007-04-22
Hello,

I've searched around the forums and I have a problem and was confused if it's a feature or not.

I have used many linux distros in the past and hats off to the Ubuntu developers... it's a great solution and each release continues to impress me.

Ok now for my question.

I followed the various wikis online to get WoW running in linux and have hit a snag.  I had repeated problems with the game hard locking my pc.  It was to the point that even the reset button on the front of the case would not reset the pc, I had to flip the power supply switch on the back of the case.

I seemed to somewhat resolve the hard lock issues but performance is absolutely abysmal.

Specs

Intel Core2 Duo 6400 oc'd to 3ghz
2GB ddr2 ram
ati xt1900 512mb ram

In Shattrah City I would average 8-15 fps and in Orgrimmar I would clock in around 35-40 which is about 1/3 of windows performance.  In Windows XP or Vista I average 40ish in Shattrah with lots of models on screen and 120'ish in Orgrimmar.

I ran glxgears and my FPS is in the neighborhood of 11000.

Is this type of performance to be expected in Linux or is something wrong?

---

### Post by hikaricore on 2007-04-22
Keep in mind that you're running WoW in an environment that it was not designed to run under.
Your system specs (video card aside) are great so you shouldn't have much trouble.

Also you should be running in OpenGL mode for the best results, does your card support OpenGL fully?

The ATI drivers released for linux have plauged this forum due to their instability, this is not an linux issue, but due to the fact that the drivers themselves are badly written for linux thanks to your hardware vendor.
Don't get me wrong I'm not snubbing you because of your video card situation, but just do a search of this forum for "ATI game" or "ATI WoW" and see what happens.  >.<

There are dozens of settings you can change to increase performance have you tried all the suggestions in the community howto?  Also you may need to disable full screen glow effects and lower some of the graphical options in WoW, possibly the resolution as well.  I'm aware the game crashes in OpenGL mode when changing graphic settings, this is well documented and there are workarounds for this issue (chaning them in d3d mode or doing it manually in config.wtf)

If you're still not happy with the perfomance of WoW, inform blizzard that their pretend ignorance of the linux gaming community is growing tiresome.
There was originally a linux port of WoW during beta but it vanished quietly into the night.  GG blizzard.

[http://www.wowwiki.com/Linux/Wine#Troubleshooting](http://www.wowwiki.com/Linux/Wine#Troubleshooting)
[http://help.ubuntu.com/community/WorldofWarcraft](http://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by Swarms on 2007-04-22
> **hikaricore said:**
> Keep in mind that you're running WoW in an environment that it was not designed to run under.
Your system specs (video card aside) are great so you shouldn't have much trouble.

Also you should be running in OpenGL mode for the best results, does your card support OpenGL fully?

The ATI drivers released for linux have plauged this forum due to their instability, this is not an linux issue, but due to the fact that the drivers themselves are badly written for linux thanks to your hardware vendor.
Don't get me wrong I'm not snubbing you because of your video card situation, but just do a search of this forum for "ATI game" or "ATI WoW" and see what happens.  >.<

There are dozens of settings you can change to increase performance have you tried all the suggestions in the community howto?  Also you may need to disable full screen glow effects and lower some of the graphical options in WoW, possibly the resolution as well.  I'm aware the game crashes in OpenGL mode when changing graphic settings, this is well documented and there are workarounds for this issue (chaning them in d3d mode or doing it manually in config.wtf)

If you're still not happy with the perfomance of WoW, inform blizzard that their pretend ignorance of the linux gaming community is growing tiresome.
There was originally a linux port of WoW during beta but it vanished quietly into the night.  GG blizzard.

[http://www.wowwiki.com/Linux/Wine#Troubleshooting](http://www.wowwiki.com/Linux/Wine#Troubleshooting)
[http://help.ubuntu.com/community/WorldofWarcraft](http://help.ubuntu.com/community/WorldofWarcraft)

To workaround crashes when changing graphical settings in OpenGL, [http://www.wowinterface.com/downloads/info5202-ApplyToForehead.html](http://www.wowinterface.com/downloads/info5202-ApplyToForehead.html)

---

### Post by thejayjay on 2007-04-22
The forehead addon is pretty sweet, it fixed the graphical adjustment problems.

I have tried adjusting various settings to see if the performance would improve and I would see little to no change.  I had hoped I would see acceptable framerates (30+ while raiding) to not use both os's blah blah blah.  Not a big deal but after spending hours attempting to get WoW and ATI to play nice together I was reminded just how bad the ATI drivers were compared to Nvidia.

I wasn't aware if you could actually see acceptable performance in linux or if that was a complete joke.

---

### Post by Death_Sargent on 2007-04-22
Ok i have a crappier computer than you and i always get 30 fps. the trick is proprietary drivers and cedega man.

Also if your using AIGXL or Xgl for your desktop you may want to look at this [How To Game With XGL]("http://ubuntuforums.org/showthread.php?t=176636")

---

### Post by lakersforce on 2007-04-22
> **Death_Sargent said:**
> Ok i have a crappier computer than you and i always get 30 fps. the trick is proprietary drivers and cedega man.

I get the same framerate as you, but I use wine...hehe, guess I saved some money there :)

---

### Post by podfish on 2007-04-22
I would bet that your crashes are more hardware related -- try scaling back the cpu overclock, and any funky memory timings you may have, and try again.  Then, if you must overclock, make incremental increases, testing for stability each time.

---

