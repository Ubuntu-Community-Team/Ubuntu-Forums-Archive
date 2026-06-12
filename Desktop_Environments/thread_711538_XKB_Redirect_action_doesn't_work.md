---
title: "XKB Redirect action doesn't work"
date: 2008-02-29
forum: Desktop Environments
---

### Post by Vitel on 2008-02-29
I own a notebook, which keyboard doesn't have Home, End, PgUp and PgDown keys. It's quite awkwardly. Therefore I want to bind these
keys to the combinations of Ctrl_L and arrow keys.
There is a howto describing that desired bindings can be realized in XKB compat configuration:
[http://ubuntuforums.org/showthread.php?t=270398](http://ubuntuforums.org/showthread.php?t=270398)
I've modified xkb configs (see attachments) according to this tip, but Home/End/etc keys don't work - xev still returns the same Up/Down/Left/Right keysyms.
Have I made a mistake in config files?

Ububtu 7.10, Fujitsu U810.

---

### Post by lonelocust on 2008-03-18
Hey, sorry I can't help, but I do have a couple questions for you.  I just bought a Fujitsu u810 (it should arrive Friday) and have been doing some reading.  It looks like the touchscreen doesn't work with Ubuntu, what has your experience been?  Also have you solved the problem you posted here?

Thanks

---

### Post by Vitel on 2008-03-24
Hi lonelocust,
> It looks like the touchscreen doesn't work with Ubuntu, what has your experience been?
On Ubuntu 7.10 touchscreen doesn't work out of the box, but there are two drivers available:
evtouch and synaptics.
Installation of the first one is described here:
[http://forum.kuchingosc.org/viewtopic.php?f=13&t=286](http://forum.kuchingosc.org/viewtopic.php?f=13&t=286)
Currently the link seems to be broken, but it's stored in google cache, the first link here:
[http://www.google.com/search?hl=en&q=kuchingosc+u1010&btnG=%D0%9F%D0%BE%D0%B8%D1%81%D0%BA+%D0%B2+Google&lr=&aq=f](http://www.google.com/search?hl=en&q=kuchingosc+u1010&btnG=%D0%9F%D0%BE%D0%B8%D1%81%D0%BA+%D0%B2+Google&lr=&aq=f)

The second one works out of the box on 8.04 Alpha. You should calibrate it via xorg.conf parameters for now, because gsynaptics calibrator doesn't work.

> Also have you solved the problem you posted here?Not yet

Here is a couple of useful links for you:
[http://www.umpcportal.com/modules/newbb/viewtopic.php?topic_id=2202&forum=16](http://www.umpcportal.com/modules/newbb/viewtopic.php?topic_id=2202&forum=16)
[http://www.oesf.org/forum/index.php?showtopic=23835](http://www.oesf.org/forum/index.php?showtopic=23835)

---

