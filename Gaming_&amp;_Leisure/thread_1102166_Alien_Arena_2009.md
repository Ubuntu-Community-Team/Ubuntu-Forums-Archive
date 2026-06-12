---
title: "Alien Arena 2009"
date: 2009-03-21
forum: Gaming &amp; Leisure
---

### Post by Irritant on 2009-03-21
[[img]http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_1_s.jpg[/img]](http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_1.jpg) [[img]http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_2_s.jpg[/img]](http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_2.jpg) [[img]http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_7_s.jpg[/img]](http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_7.jpg) [[img]http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_4_s.jpg[/img]](http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_4.jpg)
[[img]http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_5_s.jpg[/img]](http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_5.jpg) [[img]http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_6_s.jpg[/img]](http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_6.jpg) [[img]http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_3_s.jpg[/img]](http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_3.jpg) [[img]http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_8_s.jpg[/img]](http://icculus.org/alienarena/rpa/mediathumbs/aa2k9_8.jpg)

Should be released in June or so.  Renderer has continued to receive extensive overhaul as in the previous two releases and will continue to do so.  All per-pixel effects are using GLSL now, and the performance is vastly better, talking like 300-500 percent better when everything is enabled(of course the percentages are high because all the old fixed-function crap sucked).  Going to be three new player models, and probably around a dozen new maps, plus alot of client side enhancements to make the game have a nicer, polished feel.  If you use SVN you can check out alot of this svn://svn.icculus.org/alienarena/trunk

---

### Post by izizzle on 2009-03-21
Looks sweet. Can't Wait!

More information here: [http://www.moddb.com/games/alien-arena-2008/news/alien-arena-2009-progressing-towards-summer-release](http://www.moddb.com/games/alien-arena-2008/news/alien-arena-2009-progressing-towards-summer-release)

---

### Post by Perfect Storm on 2009-03-21
Aye, Alien Arena is one of the game I enjoy besides World of Padman.


Looking forward for 2009.

---

### Post by Sadaiyappan on 2009-03-21
not to be an *** but the graphics look terrible, what engine does this use?

---

### Post by tommcd on 2009-03-21
From the screen shots I thought the graphics looked pretty good. I'm not all that fussy about that though. If the game is cool then I can live with mediocre graphics. The last time I played Alien Arena was perhaps 1-2 years ago. It looks like the graphics have greatly improved since then. I will check out the new version when it is released.

---

### Post by MaxIBoy on 2009-03-21
> **Sadaiyappan said:**
> not to be an *** but the graphics look terrible, what engine does this use?CRX, an engine developed by Irritant and a few other developers specifically for use in the game.

P.S.: Did you know that if you actually clicked on those little pictures, you get bigger ones? And if your mouse pointer has a magnifying glass with a little "plus" sign in it, you can click to get an even bigger picture?

---

### Post by hikaricore on 2009-03-21
> **Sadaiyappan said:**
> not to be an *** but the graphics look terrible, what engine does this use?

Please show us the game/engine that YOU designed which is better.  k?

---

### Post by Irritant on 2009-03-22
> **Sadaiyappan said:**
> not to be an *** but the graphics look terrible, what engine does this use?

Alrighty then :)  In all seriousness though, compared to what do they look "terrible"?  I only ask this because I'm always looking to improve the game, and I do value people's honest opinions(as long as they are honest).

---

### Post by ELD on 2009-03-22
Looking good may try it again when it is released.

---

### Post by jpeddicord on 2009-03-22
> **Irritant said:**
> Alrighty then :)  In all seriousness though, compared to what do they look "terrible"?  I only ask this because I'm always looking to improve the game, and I do value people's honest opinions(as long as they are honest).

I don't see how they look terrible either; it definitely looks to be one of the prettiest FPSes on Linux. Hope the graphics quality is adjustable though because my GMA950 probably can't handle all of that. ;)

---

### Post by MaxIBoy on 2009-03-22
Yeah, it's adjustable. Although, I think it's becoming less and less optimized for older platforms and more and more optimized to take advantage of newer graphics cards.

In general, the game is more CPU-bound than GPU-bound. My GMA950 laptop chokes pretty bad on this game, but mostly because of the 1.7 Ghz Core 2 Duo, not because of the chipset. Slight performance improvement if you set "sys_affinity" to  "1." This allows the game to run on only one core (it's not really parallelized.) Since more processes tend to go for core 0, putting it on core 1 will give it more room to breathe.

---

### Post by Irritant on 2009-03-22
It's definitely very adjustable.  In fact, to address concerns about older hardware, we reinserted some legacy code after discoving how the changes affected older hardware adversly, so if you do have say pre 2003 era hardware, the game will still run as well as before if you run on low settings(or set the r_legacy cvar).  The major performance increases are going to be for modern hardware at this point.  The high end effects like per-pixel lighting have been moved into GLSL replacing the horrendously slow fixed function routines, and everything is now using vertex arrays and GL_TRIANGLE rather than GL_TRIANGLE_STRIP/FAN(except for that legacy code I mentioned, because that is a sore area for older hardware).  For my purposes, I tested on a NV 9800GTX and ATI 1400XP(mobility), and saw dramatic changes in peformance with per-pixel lighting.  It went from being nearly unplayable on both rigs to being something I leave on even during FFA matches.  With the changes from GL_TRIANGLE_STRIP to GL_TRIANGLE alone, I had an avg FPS jump of 25% on both chipsets.  

Ultimately there are some areas that we are still working on in regards to peformance, as well as visual effects, so I really appreciate any testing feedback that people can give, positive or negative.

---

### Post by ELD on 2009-03-23
Well keep up the good work dude :)

---

