---
title: "Compiz-fusion only renders partial desktop??"
date: 2007-09-12
forum: Desktop Effects &amp; Customization
---

### Post by weizilla on 2007-09-12
I have an ATI Radeon R250 [Mobility FireGL 9000]  video card on my laptop using the ati/radeon open source drivers. I can't use the fglrx drivers because the new one doesn't support my video card. I have AIGLX set as true in my xorg file and direct rendering works. I read that xgl only works with fglrx drivers so i'm not using that.

i installed the latest version of compiz-fusion and it works except there are a few problems. It seems all the effects (cube, animations) work fine and look smooth but the ubuntu toolbars and window boarders disappear. I used this installation how-to: [http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)

However, the **biggest** problem is that it only renders about 3/4 of my desktop. The right 1/4 of my desktop never renders correctly and if i have the cube enabled, it displays the cube background. It does this regardless of my screen resolution too. I have attached a picture showing you what it looks like. 

I've looked up this problem and tried using different drivers but no luck.
Does anyone know what's going on or how to fix this problem??!?

I have to solve this problem before I get around to solving the window border problem as there's no point in using compiz-fusion otherwise.

---

### Post by weizilla on 2007-09-12
I just tired to use Desktop Effects on a Live CD. Same problem. It seems like it's just having problem rendering the full screen because when the cube rotates, it's rotates the 3/4 of the screen that's rendered properly. The 1/4 bad part seems to just be part of the background.

---

### Post by Pathfinder_ on 2007-09-22
I had the same problem and changed my depth to 16-bit and it worked fine after that.

---

### Post by Vadi on 2007-09-22
Odd. Try posted in the compiz fusion forums (forum.compiz-fusion.org)

---

### Post by Newbie1978 on 2007-10-02
I use this simple steps and bingo! got it to work pretty quick I may add, it seems so simple now but sure I have a lot of frustration while trying to get it up and running

Type on a terminal:

sudo aptitude install emerald emerald-themes

compiz --replace emerald

---

