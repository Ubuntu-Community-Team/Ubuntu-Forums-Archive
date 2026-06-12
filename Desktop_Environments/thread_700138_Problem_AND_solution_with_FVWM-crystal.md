---
title: "Problem AND solution with FVWM-crystal"
date: 2008-02-18
forum: Desktop Environments
---

### Post by aletheianalex on 2008-02-18
I thought I would post this here in case anyone else runs into this problem and comes here for an answer.

I installed FVWM-crystal over FVWM-gnome in Ubuntu 7.10.  I also installed ( as I always do) Debian "menu" .  Upon typing 

> update-menus

I got an error:

> sh: illegal option -r
sh: illegal option -r
sh: illegal option -r
sh: illegal option -r
sh: illegal option -r
sh: illegal option -r
etc...

Repeating over and over and over again.  I poked around a bit and discovered that fvwm-crystal's menu update script does not play well with DASH... which I did not realize until this event was the default system shell in Ubuntu.... and the -r option is not supported.

I solved the problem by switching the default /bin/sh  to BASH since that is what I am used to anyway.  There may be a less intrusive solution though.   Hope that helps someone...

---

