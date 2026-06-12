---
title: "ATI + restricted driver + XGL + (Compiz | Beryl)"
date: 2007-04-27
forum: Desktop Effects &amp; Customization
---

### Post by Pasto on 2007-04-27
I've been looking the forum for someone with a problem like this, but didn't find a thing. 

I've installed Feisty in a dell 1501 inspiron, which has an ati x1150 card. Installed the restricted drivers, everything works ok so far. So I tried to put beryl, downgraded so it can work with XGL. At first everything worked ok, but then after a few restarts, some weird graphic glitches started appearing, and I couldn't understand why. Removed beryl, installed compiz, and after a while the same. Format partition, reinstalled feisty (yeah a bit extreme I know) and again, after a few restarts the ugly glitches appear back.

Before I had Vista on the laptop and I had absolutely no problems with OpenGL, so it makes me think that shouldn't be any problem with the video card. In Feisty I tried playing openarena and also no problems, everything looks fine. So I guess my problem is just with XGL and (Compiz or Beryl).

I'm not even sure *what* is the correct word to describe my problem, maybe 'glitch' is not the more appropiate one. I'm attaching a desktop screenshot to show the problem.

My xorg.conf is just as feisty left it (Composite 0, using fglrx driver). This only happens by using an XGL Session and activating either Beryl or Compiz. And *sometimes* everything is ok. But most of the time it isn't.

Sorry if this issue has already been posted, couldn't find it!

---

### Post by Pasto on 2007-04-27
Mmmm, I think my problem could be this, but not sure: [http://ubuntuforums.org/showthread.php?t=292142](http://ubuntuforums.org/showthread.php?t=292142)

If it is, it says it can be fixed downgrading fglrx, but I'm not completely sure how to do that. I'll try though.

---

