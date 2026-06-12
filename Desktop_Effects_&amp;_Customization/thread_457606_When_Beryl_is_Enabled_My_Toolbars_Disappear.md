---
title: "When Beryl is Enabled My Toolbars Disappear"
date: 2007-05-28
forum: Desktop Effects &amp; Customization
---

### Post by dez_cole on 2007-05-28
When i enable beryl all the tool bars for all the program windows disappear. Well to explain farther the bars that has the minimize/maximize/close buttons on it doesn't exist in beryl for me. the actual tool bars with the applications/places/system/ windows are there but the tool bars for program windows aren't. 

How can i get my tool bars back???
Sorry for the vague description of my problem. I'm a little bit of a noob to linux.

Thanks.

Also im running 7.04

---

### Post by zero244 on 2007-05-28
If you seach this forum there is a possible fix for that problem..............let me guess your using a Nvidia card right.
I had Berly running pretty good with a ATI9600 card, when I upgraded to a Nvidia card all hell broke lose.
Beryl crashes within minutes........and I had the missing Title Bars too.
I dont think Beryl is even close to prime time. Its very cool and I like the effects but its not worth the hassle of having a unstable system for eye candy.
I like Gnome just the way it is........one thing I wish Gnome had was Shadows on the Windows like KDE....if it had that I wouldnt even bother with Beryl.

---

### Post by dez_cole on 2007-05-28
yeah i have a nvidia card, 6600 gt.
who would think it would be easier to run beryl on an ati card then a nvidia card.

also im running 7.04

---

### Post by tincho1024 on 2007-10-12
so, is there a solution for this problem?

I am using Feisty Fawn with a nvidia 6800XT and my toolbars are totally gone

thx 4 all :)

---

### Post by Forlong on 2007-10-13
> **tincho1024 said:**
> I am using Feisty Fawn with a nvidia 6800XT and my toolbars are totally gone
Try this in the terminal:
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
(you have to restart X to make the changes work)

---

