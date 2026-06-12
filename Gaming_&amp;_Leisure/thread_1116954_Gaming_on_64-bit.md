---
title: "Gaming on 64-bit"
date: 2009-04-05
forum: Gaming &amp; Leisure
---

### Post by MaximB on 2009-04-05
Hello

I have a strong quad core PC with new ATI video card.
When the new Ubuntu version comes out I want to install the 64-bit version, but first I have a few questions...

If I understand correctly all you need to run 32-bit games on 64-bit machine is "ia32-libs" .
Is it correct for all games or some games won't run at all / or needs to be configured/installed otherwise ?

Would I feel improvement / slowness when running 32-bit games under 64-bit OS ?

Would games that have a native 64-bit client run better then the 32-bit ones ?

Thanks
Maxim.

---

### Post by Grishka on 2009-04-05
> **MaximB said:**
> Hello

I have a strong quad core PC with new ATI video card.
When the new Ubuntu version comes out I want to install the 64-bit version, but first I have a few questions...

If I understand correctly all you need to run 32-bit games on 64-bit machine is "ia32-libs" .
Is it correct for all games or some games won't run at all / or needs to be configured/installed otherwise ?

Would I feel improvement / slowness when running 32-bit games under 64-bit OS ?

Would games that have a native 64-bit client run better then the 32-bit ones ?

Thanks
Maxim.

ia32-libs doesn't contain every possible 32-bit library, just the ones considered most essential. running some 32-bit games will require using getlibs ([http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)). if the game is unmaintained, it can sometimes need some older, obsolete libraries. getlibs won't work for libraries that are not in the current repo, so sometimes it's necessary to download their proper 32-bit versions manually from [http://packages.ubuntu.com/](http://packages.ubuntu.com/), and put them in /usr/lib32. most 32-bit programs will run using one of these methods. about speed, idk. it all works pretty fast for me.

---

### Post by Naiki Muliaina on 2009-04-05
> **MaximB said:**
> 
Is it correct for all games or some games won't run at all / or needs to be configured/installed otherwise ?

I play a lot of games, i haven't found any that do not work yet. There probably is, but i haven't met it yet ^^


> **MaximB said:**
> Would I feel improvement / slowness when running 32-bit games under 64-bit OS ?

I have a good processor and 8gb of ram. Everything runs quickly for me. If there is some sort of slowdown, ive never experienced it.

> **MaximB said:**
> Would games that have a native 64-bit client run better then the 32-bit ones ?

They can make the best of your processor and ram (if you have more then 3.5gb or whatever it is 32bit's max is). In my opinion having a 64 bit PC and running 32 bit on it, is the equivalent of spending £1000 on a decent bike, then riding it 50 foot to your shops once a month. :)

On a brief footnote. I have noticed a lot more people using 64 bit this last 6 months. Jaunty looks like it will have a high rate of 64 bit downloads. Perhaps by this general shift its a sign that 64 bit is ready for the masses.

Extra footnote, have you seen this poll yet? [http://ubuntuforums.org/showthread.php?t=1114047](http://ubuntuforums.org/showthread.php?t=1114047).  The world is ready for 64 bit linux.

:KS:guitar::KS

---

### Post by Chemical Imbalance on 2009-04-05
Just to add:

A lot of games are not optimized for more than one core.  I find that a lot of games I run (like Urban Terror) only utilize one core--at a high percentage.  
Valve's newer games I believe are multi-processor enabled however.  
It really irks me that in 2009 applications are still only being written for one core when almost all the processors in stores now are at least hyper-threading capable if not dual core or quad core.

---

### Post by Melcar on 2009-04-05
All games run on one core (in Linux at least). It still helps to have at least one extra core since you can run stuff in the background while the game hogs the other core.

---

### Post by Polygon on 2009-04-05
> **Chemical Imbalance said:**
> Just to add:

A lot of games are not optimized for more than one core.  I find that a lot of games I run (like Urban Terror) only utilize one core--at a high percentage.  
Valve's newer games I believe are multi-processor enabled however.  
It really irks me that in 2009 applications are still only being written for one core when almost all the processors in stores now are at least hyper-threading capable if not dual core or quad core.

its not as easy as saying 'k my game will be dual core', it is supposedly a lot of work to make something run on two cores, and actually get a performance boost out of it.

---

### Post by Chemical Imbalance on 2009-04-05
> **Polygon said:**
> its not as easy as saying 'k my game will be dual core', it is supposedly a lot of work to make something run on two cores, and actually get a performance boost out of it.

Thanks for making my post sound stupid.  As I already mentioned, Valve already implements this in their newer games. [http://arstechnica.com/gaming/news/2006/11/valve-multicore.ars](http://arstechnica.com/gaming/news/2006/11/valve-multicore.ars)

Yes it is a lot of work, but it needs be implemented more.

---

