---
title: "Feisty boots with ultra-high screen res; why?"
date: 2007-04-28
forum: Desktop Environments
---

### Post by imagerodeo on 2007-04-28
Can someone explain how Ubuntu (Feisty) decides what screen res to use on boot? Pointers to specific files would be appreciated. I'm a linux noob; I get the basics, but I haven't yet figured out where all of the config is sitting.

My problem: every time I boot, I land at the login screen in very high res; I think it's 1800x1200. My monitor scales it down to the native res (1280x1024). As soon as I log in, my desktop comes up as 1280x1024, which is what I set. However, I can't find any setting to change the res of that initial login screen.

Btw, this only started happening after I installed Feisty. I'm using the restricted ATI driver.

---

### Post by JediSpam on 2007-04-28
this information is in your xorg.conf file. i am a beginner as well when it comes to setup and I usually ask someon as well. You need to edit that file to force your pc into whatever resolution you would like to run

---

### Post by imagerodeo on 2007-04-29
OK... I dug into xorg.conf and cleaned it up. There were two Screen, Device and Monitor sections; one of each is enough (I have exactly one graphics card and one monitor. For ref ("man xorg.conf" for details):

Monitor = monitor
Device = graphics card
Screen = binding between the two, plus res choices, etc.

My active Screen section didn't have any resolution settings (Feisty upgrade bug?), so I guess X11 decided to boot on something silly like 1776x1280 (X11 bug?). In any case, I was able to diff the various versions, figure out what happened, and build a clean xorg.conf that boots into 1280x1024 - my native res.

Perhaps someone will benefit from my spelunking. Enjoy.

---

