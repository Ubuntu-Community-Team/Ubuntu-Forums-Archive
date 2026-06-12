---
title: "Missing Fonts, or incompatibilities?"
date: 2012-02-17
forum: Desktop Environments
---

### Post by Grafeit on 2012-02-17
I have been using Ubuntu 11.10 for about 2 weeks on a Toshiba Satellite and there have been troubles with the fonts, however, they have grown more frequent with the most recent update. (I installed 35 updates just tonight)

Here are some things that I have noticed:

*Happens in Firefox and in Apps from the USC (software center) but not in Libre
*Doesn't seem to affect certain keys or letters, seems to be happening at random places all over the screen
*Happens more after an update, A LOT more.
*Doesn't affect images, strictly font, and after changing the fonts for firefox (don't know how to do so for other installed apps) the issue persist.

I will attempt to attach a screen captures...sometimes I mess up when trying to attach screen captures. :/


AaBbCcDdEeFfGgHhIiJjKkLlMmNnOoPpQqRrSsTtUuVvWwXxYyZz

---

### Post by Grafeit on 2012-02-17
Actually now it seems specific to the letters...which is odd, it wasn't before the updates. Please help me figure this crap out! It's so annoying!

*EDIT*
NVM, it's not related to the letters.

AaBbCcDdEeFfGgHhIiJjKkLlMmNnOoPpQqRrSsTtUuVvWwXxYyZz

---

### Post by Copper Bezel on 2012-02-17
Yeah, it looked like it was just e, c, and t from the first set of screenshots, so thanks for the additional information. It's strange that LO works and Firefox doesn't, when both use Qt font rendering. Does it affect any of the applications that came with the system? (I ask because they almost all use GTK rather than Qt, and together, those are the two UI toolkits Ubuntu uses.)

---

### Post by Grafeit on 2012-02-18
> **Copper Bezel said:**
> Yeah, it looked like it was just e, c, and t from the first set of screenshots, so thanks for the additional information. It's strange that LO works and Firefox doesn't, when both use Qt font rendering. Does it affect any of the applications that came with the system? (I ask because they almost all use GTK rather than Qt, and together, those are the two UI toolkits Ubuntu uses.)

I doesn't affect any system applications. (I struggled so bad to read your post lol)

---

### Post by Grafeit on 2012-02-20
I installed the advanced settings thing through terminal. I changed the font render to 1.1 and that seems to have fixed it for the most part. However upon changing that, my desktop items fonts have been messed up. (Yes, I've restarted the comp) It's not as bad as Firefox and other apps were, but still a tad off.

---

### Post by Copper Bezel on 2012-02-21
Well, that's something, but it still sounds irritating. Hey, what happens if you do [_this_]("http://linuxtweaking.blogspot.com/2011/01/ubuntu-10x-firefox-font-rendering-fix.html")?

---

